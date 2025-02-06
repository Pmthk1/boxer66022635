pipeline {
    agent any
    stages {      
        stage("Copy file to Docker server") {
            steps {
                // ใช้ path ที่ตรงกับ workspace จริง 43.208.154.11
                sh "scp -r /var/lib/jenkins/workspace/66022635-html/* root@43.209.4.218:~/admin-boxer"
            }
        }
        
        stage("Build Docker Image") {
            steps {
                // ใช้ path ที่ตรงกับ workspace จริง
                ansiblePlaybook playbook: '/var/lib/jenkins/workspace/66022635-html/playbooks/build.yaml'
            }    
        } 
        
        stage("Create Docker Container") {
            steps {
                // ใช้ path ที่ตรงกับ workspace จริง
                ansiblePlaybook playbook: '/var/lib/jenkins/workspace/66022635-html/playbooks/deploy.yaml'
            }    
        } 
    }
}
