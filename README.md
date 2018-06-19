-> Instalar o plugin Sonar Qube Scanner e Quality Gate

-> Habilitá-lo em Configurar o Jenkins > Global Configuration

    -> Clicar em Add SonarQube Scanner
    -> Em name, preencher com os dados do "tool" que está no pipeline (SonarQube Scanner)
    -> Clicar em save    

-> Configurar o servidor em Configurar o Jenkins > Confirar o Sistema:

    (Clicar em Add SonarQube para criar uma nova instância)

    Name: SonarQube Local (Esse nome é usado na função withSonarQubeEnv)
    Server URL: http://sonar_qube:9000 (Host e porta configurada no docker-compose)
    Additional analysis properties (Avançado): "sonar.sources=code_to_analyze sonar.projectKey=teste"

    O primeiro parâmetro das propriedades adicionais é o nome da pasta onde se
    encontra o projeto a ser analisado, e o segundo é uma chave de identificação
    única do projeto.

    Para cada pasta diferente é necessário adicionar uma nova instância do
    SonarQube.

    Documentação oficial:
    https://docs.sonarqube.org/display/SCAN/Analyzing+with+SonarQube+Scanner+for+Jenkins?src=sidebar

-> Criar webhook para se comunicar com o pipeline

    O stage 'Scan code' apenas gera um gatilho no servidor do SonarQube para analizar
    o código que está buildando no Jenkins. Entretanto, se aparecerem bugs, isso não
    gerará um erro no pipeline.

    Para resolver esse problema, é necessário [...]