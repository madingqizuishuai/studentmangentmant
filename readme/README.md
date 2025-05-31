# 项目名称
### VUE项目的学习与使用

## 开发软件
   ### vscode

## 学习经历
### 学习了怎么配置VUE环境，熟悉了vue的框架和基础语法，怎么创建和写readme.md文件

## 代码展示
<!DOCTYPE html>
<html lang="zh-CN">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>学生信息管理系统 - Vue</title>
  <script src="https://unpkg.com/vue@3/dist/vue.global.js"></script>
  <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
  <style>
    * {
      margin: 0;
      padding: 0;
      box-sizing: border-box;
      font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
    }
    
    body {
      background: linear-gradient(135deg, #6a11cb 0%, #2575fc 100%);
      min-height: 100vh;
      padding: 20px;
      color: #333;
    }
    
    .container {
      max-width: 1200px;
      margin: 0 auto;
    }
    
    header {
      text-align: center;
      padding: 30px 0;
      color: white;
      animation: fadeInDown 0.8s ease-out;
    }
    
    header h1 {
      font-size: 2.8rem;
      margin-bottom: 10px;
      text-shadow: 0 2px 4px rgba(0,0,0,0.2);
    }
    
    header p {
      font-size: 1.2rem;
      opacity: 0.9;
      max-width: 600px;
      margin: 0 auto;
    }
    
    .app-card {
      background: white;
      border-radius: 16px;
      box-shadow: 0 10px 30px rgba(0,0,0,0.15);
      overflow: hidden;
      margin-bottom: 30px;
      animation: fadeInUp 0.8s ease-out;
    }
    
    .toolbar {
      padding: 20px;
      display: flex;
      flex-wrap: wrap;
      gap: 15px;
      background: #f8f9fa;
      border-bottom: 1px solid #eee;
    }
    
    .search-box {
      flex: 1;
      min-width: 250px;
      position: relative;
    }
    
    .search-box input {
      width: 100%;
      padding: 12px 20px 12px 45px;
      border: 1px solid #ddd;
      border-radius: 50px;
      font-size: 16px;
      transition: all 0.3s;
    }
    
    .search-box input:focus {
      outline: none;
      border-color: #2575fc;
      box-shadow: 0 0 0 3px rgba(37, 117, 252, 0.2);
    }
    
    .search-box i {
      position: absolute;
      left: 18px;
      top: 50%;
      transform: translateY(-50%);
      color: #888;
    }
    
    .btn {
      padding: 12px 25px;
      border: none;
      border-radius: 50px;
      cursor: pointer;
      font-size: 16px;
      font-weight: 600;
      display: inline-flex;
      align-items: center;
      gap: 8px;
      transition: all 0.3s;
    }
    
    .btn-primary {
      background: linear-gradient(135deg, #6a11cb 0%, #2575fc 100%);
      color: white;
    }
    
    .btn-primary:hover {
      transform: translateY(-2px);
      box-shadow: 0 5px 15px rgba(37, 117, 252, 0.4);
    }
    
    .btn-danger {
      background: linear-gradient(135deg, #ff416c 0%, #ff4b2b 100%);
      color: white;
    }
    
    .btn-outline {
      background: transparent;
      border: 2px solid #2575fc;
      color: #2575fc;
    }
    
    .btn-outline:hover {
      background: #2575fc;
      color: white;
    }
    
    .filters {
      display: flex;
      gap: 15px;
      flex-wrap: wrap;
    }
    
    .filter-select {
      padding: 10px 15px;
      border: 1px solid #ddd;
      border-radius: 50px;
      background: white;
      font-size: 14px;
      min-width: 150px;
    }
    
    .student-grid {
      display: grid;
      grid-template-columns: repeat(auto-fill, minmax(300px, 1fr));
      gap: 25px;
      padding: 30px;
    }
    
    .student-card {
      background: white;
      border-radius: 12px;
      overflow: hidden;
      box-shadow: 0 4px 15px rgba(0,0,0,0.08);
      transition: all 0.3s ease;
      position: relative;
    }
    
    .student-card:hover {
      transform: translateY(-5px);
      box-shadow: 0 8px 25px rgba(0,0,0,0.15);
    }
    
    .student-header {
      background: linear-gradient(135deg, #43cea2 0%, #185a9d 100%);
      color: white;
      padding: 20px;
      text-align: center;
    }
    
    .student-avatar {
      width: 80px;
      height: 80px;
      border-radius: 50%;
      border: 3px solid white;
      margin: 0 auto 15px;
      background: #f0f0f0;
      display: flex;
      align-items: center;
      justify-content: center;
      font-size: 32px;
      color: #555;
    }
    
    .student-name {
      font-size: 1.4rem;
      margin-bottom: 5px;
    }
    
    .student-id {
      opacity: 0.9;
      font-size: 0.9rem;
    }
    
    .student-body {
      padding: 20px;
    }
    
    .student-info {
      display: flex;
      flex-direction: column;
      gap: 12px;
      margin-bottom: 20px;
    }
    
    .info-item {
      display: flex;
    }
    
    .info-label {
      font-weight: 600;
      min-width: 80px;
      color: #555;
    }
    
    .info-value {
      flex: 1;
    }
    
    .student-actions {
      display: flex;
      gap: 10px;
      border-top: 1px solid #eee;
      padding-top: 20px;
    }
    
    .action-btn {
      flex: 1;
      padding: 8px;
      border-radius: 8px;
      text-align: center;
      cursor: pointer;
      transition: all 0.2s;
      font-size: 14px;
    }
    
    .edit-btn {
      background: rgba(37, 117, 252, 0.1);
      color: #2575fc;
    }
    
    .edit-btn:hover {
      background: rgba(37, 117, 252, 0.2);
    }
    
    .delete-btn {
      background: rgba(255, 75, 43, 0.1);
      color: #ff4b2b;
    }
    
    .delete-btn:hover {
      background: rgba(255, 75, 43, 0.2);
    }
    
    .modal-overlay {
      position: fixed;
      top: 0;
      left: 0;
      right: 0;
      bottom: 0;
      background: rgba(0,0,0,0.5);
      display: flex;
      align-items: center;
      justify-content: center;
      z-index: 1000;
      opacity: 0;
      pointer-events: none;
      transition: opacity 0.3s;
    }
    
    .modal-overlay.active {
      opacity: 1;
      pointer-events: all;
    }
    
    .modal {
      background: white;
      border-radius: 16px;
      width: 100%;
      max-width: 500px;
      box-shadow: 0 10px 50px rgba(0,0,0,0.3);
      transform: translateY(20px);
      transition: transform 0.3s;
    }
    
    .modal-overlay.active .modal {
      transform: translateY(0);
    }
    
    .modal-header {
      padding: 20px;
      border-bottom: 1px solid #eee;
      display: flex;
      justify-content: space-between;
      align-items: center;
    }
    
    .modal-title {
      font-size: 1.4rem;
      font-weight: 600;
    }
    
    .close-btn {
      background: none;
      border: none;
      font-size: 24px;
      cursor: pointer;
      color: #888;
      transition: color 0.2s;
    }
    
    .close-btn:hover {
      color: #333;
    }
    
    .modal-body {
      padding: 25px;
    }
    
    .form-group {
      margin-bottom: 20px;
    }
    
    .form-group label {
      display: block;
      margin-bottom: 8px;
      font-weight: 500;
      color: #555;
    }
    
    .form-control {
      width: 100%;
      padding: 12px 15px;
      border: 1px solid #ddd;
      border-radius: 8px;
      font-size: 16px;
      transition: all 0.3s;
    }
    
    .form-control:focus {
      outline: none;
      border-color: #2575fc;
      box-shadow: 0 0 0 3px rgba(37, 117, 252, 0.2);
    }
    
    .modal-footer {
      padding: 20px;
      border-top: 1px solid #eee;
      display: flex;
      justify-content: flex-end;
      gap: 10px;
    }
    
    .empty-state {
      text-align: center;
      padding: 60px 20px;
      grid-column: 1 / -1;
    }
    
    .empty-state i {
      font-size: 70px;
      color: #ddd;
      margin-bottom: 20px;
    }
    
    .empty-state h3 {
      font-size: 1.5rem;
      margin-bottom: 15px;
      color: #666;
    }
    
    @keyframes fadeInUp {
      from {
        opacity: 0;
        transform: translateY(20px);
      }
      to {
        opacity: 1;
        transform: translateY(0);
      }
    }
    
    @keyframes fadeInDown {
      from {
        opacity: 0;
        transform: translateY(-20px);
      }
      to {
        opacity: 1;
        transform: translateY(0);
      }
    }
    
    @media (max-width: 768px) {
      .student-grid {
        grid-template-columns: repeat(auto-fill, minmax(250px, 1fr));
        padding: 20px 15px;
        gap: 20px;
      }
      
      .toolbar {
        flex-direction: column;
      }
      
      .search-box, .filters {
        width: 100%;
      }
      
      .btn {
        width: 100%;
        justify-content: center;
      }
    }
  </style>
</head>
<body>
  <div id="app">
    <div class="container">
      <header>
        <h1><i class="fas fa-graduation-cap"></i> 学生信息管理系统</h1>
        <p>使用Vue.js构建的学生信息增删改查应用</p>
      </header>
      
      <main>
        <div class="app-card">
          <div class="toolbar">
            <div class="search-box">
              <i class="fas fa-search"></i>
              <input type="text" v-model="searchQuery" placeholder="搜索学生...">
            </div>
            
            <div class="filters">
              <select class="filter-select" v-model="selectedMajor">
                <option value="">所有专业</option>
                <option v-for="major in majors" :value="major">{{ major }}</option>
              </select>
              
              <select class="filter-select" v-model="selectedGrade">
                <option value="">所有年级</option>
                <option v-for="grade in grades" :value="grade">{{ grade }}</option>
              </select>
            </div>
            
            <button class="btn btn-primary" @click="openAddModal">
              <i class="fas fa-plus"></i> 添加学生
            </button>
          </div>
          
          <div class="student-grid">
            <div v-if="filteredStudents.length === 0" class="empty-state">
              <i class="fas fa-user-graduate"></i>
              <h3>没有找到学生信息</h3>
              <p>尝试修改搜索条件或添加新学生</p>
            </div>
            
            <div v-for="student in filteredStudents" :key="student.id" class="student-card">
              <div class="student-header">
                <div class="student-avatar">
                  <i class="fas fa-user"></i>
                </div>
                <h2 class="student-name">{{ student.name }}</h2>
                <div class="student-id">学号: {{ student.id }}</div>
              </div>
              
              <div class="student-body">
                <div class="student-info">
                  <div class="info-item">
                    <span class="info-label">专业:</span>
                    <span class="info-value">{{ student.major }}</span>
                  </div>
                  <div class="info-item">
                    <span class="info-label">年级:</span>
                    <span class="info-value">{{ student.grade }}级</span>
                  </div>
                  <div class="info-item">
                    <span class="info-label">班级:</span>
                    <span class="info-value">{{ student.class }}</span>
                  </div>
                  <div class="info-item">
                    <span class="info-label">电话:</span>
                    <span class="info-value">{{ student.phone }}</span>
                  </div>
                  <div class="info-item">
                    <span class="info-label">邮箱:</span>
                    <span class="info-value">{{ student.email }}</span>
                  </div>
                </div>
                
                <div class="student-actions">
                  <div class="action-btn edit-btn" @click="openEditModal(student)">
                    <i class="fas fa-edit"></i> 编辑
                  </div>
                  <div class="action-btn delete-btn" @click="deleteStudent(student.id)">
                    <i class="fas fa-trash-alt"></i> 删除
                  </div>
                </div>
              </div>
            </div>
          </div>
        </div>
      </main>
    </div>
    
    <!-- 添加/编辑模态框 -->
    <div class="modal-overlay" :class="{ active: showModal }">
      <div class="modal">
        <div class="modal-header">
          <h3 class="modal-title">{{ isEditing ? '编辑学生信息' : '添加新学生' }}</h3>
          <button class="close-btn" @click="closeModal">&times;</button>
        </div>
        
        <div class="modal-body">
          <div class="form-group">
            <label>学号</label>
            <input type="text" class="form-control" v-model="currentStudent.id">
          </div>
          
          <div class="form-group">
            <label>姓名</label>
            <input type="text" class="form-control" v-model="currentStudent.name">
          </div>
          
          <div class="form-group">
            <label>专业</label>
            <select class="form-control" v-model="currentStudent.major">
              <option v-for="major in majors" :value="major">{{ major }}</option>
            </select>
          </div>
          
          <div class="form-group">
            <label>年级</label>
            <select class="form-control" v-model="currentStudent.grade">
              <option v-for="grade in grades" :value="grade">{{ grade }}级</option>
            </select>
          </div>
          
          <div class="form-group">
            <label>班级</label>
            <input type="text" class="form-control" v-model="currentStudent.class">
          </div>
          
          <div class="form-group">
            <label>电话</label>
            <input type="text" class="form-control" v-model="currentStudent.phone">
          </div>
          
          <div class="form-group">
            <label>邮箱</label>
            <input type="email" class="form-control" v-model="currentStudent.email">
          </div>
        </div>
        
        <div class="modal-footer">
          <button class="btn btn-outline" @click="closeModal">取消</button>
          <button class="btn btn-primary" @click="saveStudent">
            {{ isEditing ? '更新信息' : '添加学生' }}
          </button>
        </div>
      </div>
    </div>
  </div>

  <script>
    const { createApp, ref, reactive, computed } = Vue
    
    createApp({
      setup() {
        // 学生数据
        const students = ref([
          { id: '2023001', name: '张三', major: '计算机科学', grade: '2023', class: '1班', phone: '13800138000', email: 'zhangsan@example.com' },
          { id: '2023002', name: '李四', major: '软件工程', grade: '2023', class: '2班', phone: '13900139000', email: 'lisi@example.com' },
          { id: '2022001', name: '王五', major: '人工智能', grade: '2022', class: '1班', phone: '13700137000', email: 'wangwu@example.com' },
          { id: '2022002', name: '赵六', major: '数据科学', grade: '2022', class: '3班', phone: '13600136000', email: 'zhaoliu@example.com' },
          { id: '2021001', name: '钱七', major: '网络安全', grade: '2021', class: '2班', phone: '13500135000', email: 'qianqi@example.com' },
          { id: '2021002', name: '孙八', major: '物联网工程', grade: '2021', class: '1班', phone: '13400134000', email: 'sunba@example.com' }
        ])
        
        // 专业和年级选项
        const majors = ref(['计算机科学', '软件工程', '人工智能', '数据科学', '网络安全', '物联网工程'])
        const grades = ref(['2021', '2022', '2023'])
        
        // 搜索和过滤
        const searchQuery = ref('')
        const selectedMajor = ref('')
        const selectedGrade = ref('')
        
        // 模态框状态
        const showModal = ref(false)
        const isEditing = ref(false)
        const currentStudent = reactive({
          id: '',
          name: '',
          major: '',
          grade: '',
          class: '',
          phone: '',
          email: ''
        })
        
        // 过滤学生列表
        const filteredStudents = computed(() => {
          return students.value.filter(student => {
            const matchesSearch = student.name.toLowerCase().includes(searchQuery.value.toLowerCase()) || 
                                 student.id.toLowerCase().includes(searchQuery.value.toLowerCase())
            const matchesMajor = selectedMajor.value ? student.major === selectedMajor.value : true
            const matchesGrade = selectedGrade.value ? student.grade === selectedGrade.value : true
            
            return matchesSearch && matchesMajor && matchesGrade
          })
        })
        
        // 打开添加模态框
        const openAddModal = () => {
          resetCurrentStudent()
          isEditing.value = false
          showModal.value = true
        }
        
        // 打开编辑模态框
        const openEditModal = (student) => {
          Object.assign(currentStudent, student)
          isEditing.value = true
          showModal.value = true
        }
        
        // 关闭模态框
        const closeModal = () => {
          showModal.value = false
        }
        
        // 重置当前学生表单
        const resetCurrentStudent = () => {
          currentStudent.id = ''
          currentStudent.name = ''
          currentStudent.major = majors.value[0]
          currentStudent.grade = grades.value[0]
          currentStudent.class = ''
          currentStudent.phone = ''
          currentStudent.email = ''
        }
        
        // 保存学生
        const saveStudent = () => {
          if (isEditing.value) {
            // 更新学生
            const index = students.value.findIndex(s => s.id === currentStudent.id)
            if (index !== -1) {
              students.value[index] = { ...currentStudent }
            }
          } else {
            // 添加新学生
            students.value.push({ ...currentStudent })
          }
          showModal.value = false
        }
        
        // 删除学生
        const deleteStudent = (id) => {
          if (confirm('确定要删除这个学生吗？')) {
            students.value = students.value.filter(student => student.id !== id)
          }
        }
        
        return {
          students,
          majors,
          grades,
          searchQuery,
          selectedMajor,
          selectedGrade,
          filteredStudents,
          showModal,
          isEditing,
          currentStudent,
          openAddModal,
          openEditModal,
          closeModal,
          saveStudent,
          deleteStudent
        }
      }
    }).mount('#app')
  </script>
</body>
</html>
（代码大部分由ai生成）

## 成果展示
 地址：http://127.0.0.1:5500/src/components/student.html



界面
![alt text](image.png)

删除学生张三操作后
![alt text](image-1.png)


添加学生马9后
![alt text](image-2.png)

### 说明：点击学生信息的删除即可删除，点击添加学生输入信息后即可添加学生

## 反思
### 时间比较仓促只能通过ai写出来大部分代码，做下个项目会减少ai的使用尽量手打