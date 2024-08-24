pipeline{
    agent {label 'dotnet8'}
    options{
        timeout(time: 1, unit: 'HOURS')
    }
    triggers{
        pollSCM('* * * * *')
    }
    tools{
        dotnetsdk 'DOTNET8'
    }
    stages{
        stage('SCM'){
            steps{
                git url: 'https://github.com/manoj-406/nopCommerceAug24.git'
                branch: 'develop'
            }
        }
        stage('build'){
            steps{
                sh 'dotnet build -c Release src/Presentation/Nop.Web/Nop.Web.cspro'
                sh 'mkdir published && dotnet publish -o ./published -c Releasesrc/Presentation/Nop.Web/Nop.Web.csproj'
            }
           

        }
    }
}