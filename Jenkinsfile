pipeline {
    agent {
        kubernetes {
            cloud 'AWS'
            label 'k8s-test-agent'
            defaultContainer 'jnlp'
            yaml """
apiVersion: v1
kind: Pod
metadata:
  labels:
    jenkins/jenkins-agent: "true"
spec:
  ttlSecondsAfterFinished: 600
  tolerations:
    - key: "node-role.kubernetes.io/control-plane"
      operator: "Exists"
      effect: "NoSchedule"
  nodeSelector:
    node-role.kubernetes.io/control-plane: ""
  containers:
    - name: jnlp
      image: jenkins/inbound-agent:latest
      imagePullPolicy: Always
      resources:
        requests:
          cpu: "500m"
          memory: "512Mi"
        limits:
          cpu: "1"
          memory: "1Gi"
      volumeMounts:
        - name: workspace-volume
          mountPath: /home/jenkins/agent
  volumes:
    - name: workspace-volume
      emptyDir: {}
  restartPolicy: Never
"""
        }
    }

    stages {
        stage('Check Agent') {
            steps {
                sh 'echo ✅ Hello from Kubernetes Jenkins agent!'
                sh 'uname -a'
                sh 'whoami'
                sh 'env | grep JENKINS'
            }
        }
    }

    post {
        always {
            echo '🧹 Done - pod sẽ được giữ lại trong 10 phút để kiểm tra nếu cần.'
        }
    }
}
