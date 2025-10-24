pipeline {

agent any

tools {
maven &#39;Maven&#39;
}

parameters {
string(name: &#39;BRANCH_NAME&#39;, defaultValue: &#39;main&#39;)
string(name: &#39;BUILD_ENV&#39;, defaultValue: &#39;dev&#39;)
}

environment {
NEW_VERSION = &quot;1.3.0&quot;
}

stages {
stage(&#39;Build&#39;) {
steps {
echo &quot;Building version ${NEW_VERSION} on branch
${params.BRANCH_NAME}&quot;
//bat &quot;mvn clean package -Dversion=${NEW_VERSION}&quot;
}
}

stage(&#39;Unit Test&#39;) {
when {

expression { return params.BUILD_ENV == &#39;dev&#39; }
}
steps {
echo &#39;Running unit tests...&#39;
}
}

stage(&#39;Deploy&#39;) {
steps {
echo &#39;Deploying application...&#39;
}
}
}

post {
always {
echo &#39;Cleaning up workspace...&#39;
// deleteDir()
}
success {
echo &#39;Pipeline succeeded.&#39;
}
failure {
echo &#39;Pipeline failed.&#39;
}
}

}