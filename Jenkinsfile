pipeline {
    agent any
    stages {      
        stage("Copy file to Docker server") {
            steps {
                // ใช้ path ที่ตรงกับ workspace จริง
                sh "scp -r /var/lib/jenkins/workspace/team6-boxer/* root@13.212.94.247:~/team6_boxer"
            }
        }
        
        stage("Build Docker Image") {
            steps {
                // ใช้ path ที่ตรงกับ workspace จริง
                ansiblePlaybook playbook: '/var/lib/jenkins/workspace/team6-boxer/playbooks/build.yaml'
            }    
        } 
        
        stage("Create Docker Container") {
            steps {
                // ใช้ path ที่ตรงกับ workspace จริง
                ansiblePlaybook playbook: '/var/lib/jenkins/workspace/team6-boxer/playbooks/deploy.yaml'
            }    
        } 
    }
}
