pipeline {
    agent any
    stages {      
        stage("Copy file to Docker server") {
            steps {
                // ใช้ path ที่ตรงกับ workspace จริง
                sh "scp -r /var/lib/jenkins/workspace/admin-boxer/* root@43.209.12.132:~/admin-boxer"
            }
        }
        
        stage("Build Docker Image") {
            steps {
                // ใช้ path ที่ตรงกับ workspace จริง
                ansiblePlaybook playbook: '/var/lib/jenkins/workspace/admin-boxer/playbooks/build.yaml'
            }    
        } 
        
        stage("Create Docker Container") {
            steps {
                // ใช้ path ที่ตรงกับ workspace จริง
                ansiblePlaybook playbook: '/var/lib/jenkins/workspace/admin-boxer/playbooks/deploy.yaml'
            }    
        } 
    }
}
