<script setup>
import { ref, reactive, computed, watchEffect } from 'vue'

// 从localStorage读取数据
const loadTodos = () => {
  const savedTodos = localStorage.getItem('todos')
  return savedTodos ? JSON.parse(savedTodos) : []
}

// 保存数据到localStorage
const saveTodos = (todos) => {
  localStorage.setItem('todos', JSON.stringify(todos))
}

// 加载主题偏好
const loadTheme = () => {
  return localStorage.getItem('theme') || 'light'
}

// 保存主题偏好
const saveTheme = (theme) => {
  localStorage.setItem('theme', theme)
  if (theme === 'dark') {
    document.documentElement.classList.add('dark')
  } else {
    document.documentElement.classList.remove('dark')
  }
}

// 状态管理
const todos = reactive(loadTodos())
const newTodo = ref('')
const filter = ref('all')
const theme = ref(loadTheme())

// 切换主题
const toggleTheme = () => {
  theme.value = theme.value === 'light' ? 'dark' : 'light'
  saveTheme(theme.value)
}

// 初始化主题
watchEffect(() => {
  saveTheme(theme.value)
})

// 监听todos变化，自动保存到localStorage
watchEffect(() => {
  saveTodos(todos)
})

// 计算属性：根据筛选条件过滤任务
const filteredTodos = computed(() => {
  switch (filter.value) {
    case 'active':
      return todos.filter(todo => !todo.completed)
    case 'completed':
      return todos.filter(todo => todo.completed)
    default:
      return todos
  }
})

// 计算属性：统计未完成任务数量
const remainingCount = computed(() => {
  return todos.filter(todo => !todo.completed).length
})

// 添加任务
const addTodo = () => {
  if (newTodo.value.trim()) {
    todos.push({
      id: Date.now(),
      text: newTodo.value.trim(),
      completed: false
    })
    newTodo.value = ''
  }
}

// 切换任务完成状态
const toggleTodo = (id) => {
  const todo = todos.find(t => t.id === id)
  if (todo) {
    todo.completed = !todo.completed
  }
}

// 删除任务
const deleteTodo = (id) => {
  const index = todos.findIndex(t => t.id === id)
  if (index > -1) {
    todos.splice(index, 1)
  }
}

// 清除所有已完成任务
const clearCompleted = () => {
  const completedIds = todos.filter(todo => todo.completed).map(todo => todo.id)
  completedIds.forEach(id => deleteTodo(id))
}
</script>

<template>
  <div class="fixed inset-0 bg-blue-50 dark:bg-gray-900 flex items-center justify-center p-4 font-sans transition-colors duration-300">
    <!-- 主容器 -->
    <div class="w-full max-w-md bg-white dark:bg-gray-800 rounded-xl shadow-lg dark:shadow-xl overflow-hidden transition-colors duration-300">
      <!-- 装饰性背景 -->
      <div class="absolute top-0 left-0 w-full h-2 bg-blue-500 dark:bg-purple-600"></div>
      
      <!-- 标题区域 -->
      <div class="pt-6 pb-4 px-4 text-center relative">
        <!-- 主题切换按钮 -->
        <button
          @click="toggleTheme"
          class="absolute top-6 right-4 p-2 rounded-full bg-gray-100 dark:bg-gray-800 text-gray-600 dark:text-gray-300 transition-colors duration-200"
        >
          <svg v-if="theme === 'light'" class="w-5 h-5" fill="none" stroke="currentColor" viewBox="0 0 24 24">
            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M20.354 15.354A9 9 0 018.646 3.646 9.003 9.003 0 0012 21a9.003 9.003 0 008.354-5.646z"></path>
          </svg>
          <svg v-else class="w-5 h-5" fill="none" stroke="currentColor" viewBox="0 0 24 24">
            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M12 3v1m0 16v1m9-9h-1M4 12H3m15.364 6.364l-.707-.707M6.343 6.343l-.707-.707m12.728 0l-.707.707M6.343 17.657l-.707.707M16 12a4 4 0 11-8 0 4 4 0 018 0z"></path>
          </svg>
        </button>
        
        <h1 class="text-3xl sm:text-4xl font-bold text-blue-600 dark:text-purple-400 mb-2 tracking-tight">
          待办事项
        </h1>
        <p class="text-gray-600 dark:text-gray-400 text-base sm:text-lg">高效管理你的任务</p>
      </div>
      
      <!-- 任务输入区域 -->
      <div class="px-4 pb-6">
        <div class="flex flex-col sm:flex-row gap-3 relative">
          <input
            v-model="newTodo"
            @keyup.enter="addTodo"
            type="text"
            placeholder="今天需要做什么？"
            class="flex-1 px-5 py-3 rounded-lg border border-gray-200 dark:border-gray-600 focus:outline-none focus:ring-2 focus:ring-blue-200 dark:focus:ring-purple-500 focus:border-blue-500 dark:focus:border-purple-500 transition-all duration-200 bg-white dark:bg-gray-700 text-gray-800 dark:text-gray-200 placeholder-gray-400 dark:placeholder-gray-500 text-base sm:text-lg"
          />
          <button
            @click="addTodo"
            class="bg-blue-500 dark:bg-purple-600 text-white px-6 py-3 sm:px-7 sm:py-4 rounded-lg transition-all duration-200 hover:bg-blue-600 dark:hover:bg-purple-700 active:bg-blue-700 dark:active:bg-purple-800 font-medium text-base sm:text-lg flex items-center justify-center gap-2"
          >
            <svg class="w-5 h-5" fill="none" stroke="currentColor" viewBox="0 0 24 24">
              <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M12 4v16m8-8H4"></path>
            </svg>
            <span class="hidden sm:inline">添加</span>
          </button>
        </div>
      </div>
      
      <!-- 任务列表 -->
      <div class="max-h-[420px] overflow-y-auto scrollbar-thin scrollbar-thumb-gray-200 dark:scrollbar-thumb-gray-600 scrollbar-track-gray-50 dark:scrollbar-track-gray-800 bg-white dark:bg-gray-800">
        <transition-group name="task" tag="div" class="divide-y divide-gray-100">
          <div
            v-for="todo in filteredTodos"
            :key="todo.id"
            class="p-4 sm:p-6 flex items-center gap-4 sm:gap-5 hover:bg-gray-50 dark:hover:bg-gray-750 transition-colors duration-200 border-b border-gray-100 dark:border-gray-700"
          >
            <!-- 自定义复选框 -->
            <label class="relative flex items-center cursor-pointer">
              <input
                type="checkbox"
                v-model="todo.completed"
                class="sr-only peer"
              />
              <div class="w-6 h-6 rounded border-2 border-gray-300 dark:border-gray-600 peer-checked:border-blue-500 dark:peer-checked:border-purple-500 peer-checked:bg-blue-500 dark:peer-checked:bg-purple-600 transition-colors duration-200 flex items-center justify-center">
                <svg
                  v-if="todo.completed"
                  class="w-4 h-4 text-white"
                  fill="currentColor"
                  viewBox="0 0 20 20"
                >
                  <path fill-rule="evenodd" d="M16.707 5.293a1 1 0 010 1.414l-8 8a1 1 0 01-1.414 0l-4-4a1 1 0 011.414-1.414L8 12.586l7.293-7.293a1 1 0 011.414 0z" clip-rule="evenodd" />
                </svg>
              </div>
            </label>
            
            <!-- 任务文本 -->
            <span
              :class="[
                'flex-1 text-lg font-medium transition-all duration-300',
                todo.completed 
                  ? 'text-gray-400 dark:text-gray-500 line-through line-through-offset-4' 
                  : 'text-gray-800 dark:text-gray-200 hover:text-blue-500 dark:hover:text-purple-400'
              ]"
            >
              {{ todo.text }}
            </span>
            
            <!-- 删除按钮 -->
            <button
              @click="deleteTodo(todo.id)"
              class="text-gray-300 dark:text-gray-500 hover:text-red-500 dark:hover:text-red-400 transition-colors duration-200 p-2 rounded-full hover:bg-red-50 dark:hover:bg-red-900/20"
            >
              <svg xmlns="http://www.w3.org/2000/svg" class="h-5 w-5" viewBox="0 0 20 20" fill="currentColor">
                <path fill-rule="evenodd" d="M9 2a1 1 0 00-.894.553L7.382 4H4a1 1 0 000 2v10a2 2 0 002 2h8a2 2 0 002-2V6a1 1 0 100-2h-3.382l-.724-1.447A1 1 0 0011 2H9zM7 8a1 1 0 012 0v6a1 1 0 11-2 0V8zm5-1a1 1 0 00-1 1v6a1 1 0 102 0V8a1 1 0 00-1-1z" clip-rule="evenodd" />
              </svg>
            </button>
          </div>
        </transition-group>
        
        <!-- 空任务状态 -->
        <div v-if="todos.length === 0" class="p-12 text-center">
          <div class="inline-flex items-center justify-center w-20 h-20 bg-gray-100 dark:bg-gray-800 rounded-full mb-6">
            <svg xmlns="http://www.w3.org/2000/svg" class="h-10 w-10 text-gray-400 dark:text-gray-500" fill="none" viewBox="0 0 24 24" stroke="currentColor">
              <path stroke-linecap="round" stroke-linejoin="round" stroke-width="1.5" d="M9 5H7a2 2 0 00-2 2v12a2 2 0 002 2h10a2 2 0 002-2V7a2 2 0 00-2-2h-2M9 5a2 2 0 002 2h2a2 2 0 002-2M9 5a2 2 0 012-2h2a2 2 0 012 2" />
            </svg>
          </div>
          <h3 class="text-xl font-semibold mb-3 text-gray-500 dark:text-gray-400">还没有任务</h3>
          <p class="text-gray-400 dark:text-gray-500">开始添加你的任务来组织生活吧！</p>
        </div>
      </div>
      
      <!-- 任务统计和筛选 -->
      <div v-if="todos.length > 0" class="p-4 sm:p-6 bg-blue-50 dark:bg-gray-800 border-t border-gray-100 dark:border-gray-700">
        <!-- 统计信息 -->
        <div class="text-sm sm:text-base text-gray-700 dark:text-gray-400 mb-6 text-center font-medium">
          剩余 {{ remainingCount }} 项任务
        </div>
        
        <!-- 筛选按钮 -->
        <div class="flex flex-wrap gap-3 justify-center mb-6">
          <button
            v-for="(type, index) in [
              { key: 'all', label: '全部' },
              { key: 'active', label: '未完成' },
              { key: 'completed', label: '已完成' }
            ]"
            :key="index"
            @click="filter = type.key"
            :class="[
              'px-5 py-2.5 rounded-lg text-sm font-medium transition-colors duration-200',
              filter === type.key
                ? 'bg-blue-500 dark:bg-purple-600 text-white'
                : 'bg-white dark:bg-gray-700 text-gray-600 dark:text-gray-300 hover:bg-gray-100 dark:hover:bg-gray-750 border border-gray-200 dark:border-gray-600'
            ]"
          >
            {{ type.label }}
          </button>
        </div>
        
        <!-- 清除已完成任务按钮 -->
        <div class="text-center">
          <button
            @click="clearCompleted"
            class="text-sm font-medium text-gray-600 dark:text-gray-400 hover:text-red-500 dark:hover:text-red-400 transition-colors duration-200 inline-flex items-center gap-2"
          >
            <svg class="w-4 h-4" fill="none" stroke="currentColor" viewBox="0 0 24 24">
              <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M19 7l-.867 12.142A2 2 0 0116.138 21H7.862a2 2 0 01-1.995-1.858L5 7m5 4v6m4-6v6m1-10V4a1 1 0 00-1-1h-4a1 1 0 00-1 1v3M4 7h16"></path>
            </svg>
            <span>清除已完成</span>
          </button>
        </div>
      </div>
    </div>
  </div>
</template>

<style scoped>
/* 自定义滚动条 */
.scrollbar-thin {
  scrollbar-width: thin;
}

.scrollbar-thumb-gray-200::-webkit-scrollbar-thumb {
  background-color: #e5e7eb;
  border-radius: 9999px;
}

.scrollbar-track-gray-50::-webkit-scrollbar-track {
  background-color: #f9fafb;
  border-radius: 9999px;
}

/* 任务项动画 */
.task-enter-active,
.task-leave-active {
  transition: all 0.5s cubic-bezier(0.16, 1, 0.3, 1);
}

.task-enter-from {
  opacity: 0;
  transform: translateY(-30px) scale(0.9) rotateX(10deg);
}

.task-leave-to {
  opacity: 0;
  transform: translateX(100px) scale(0.95) rotateY(20deg);
}

.task-move {
  transition: transform 0.5s cubic-bezier(0.16, 1, 0.3, 1);
}
</style>


