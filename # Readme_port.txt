# Teste de entrevista de infraestrutura em nuvem

O objetivo deste teste é "conteinerizar" um aplicativo de exemplo e escrever o código necessário para executá-lo em um cluster kubernetes.

## Entrega

Para enviar o código, publique-o em um repositório público do github ou em um arquivo compactado com todo o conteúdo que permita que o código seja executado. Sinta-se à vontade para adicionar um arquivo README.md com instruções.

## Critério de avaliação

O código enviado será utilizado na entrevista técnica e você será questionado sobre as decisões tomadas na implementação.

O código neste repositório é escrito de forma a facilitar o desenvolvimento local, o que torna práticas inadequadas ao executá-lo em um ambiente remoto como um servidor de produção.
Altere (adicione, mova, remova, modifique, etc) quaisquer arquivos neste repositório para atender aos requisitos da próxima seção, enquanto entrega código de **grau de produção**, com o que você entende serem as melhores práticas, considerando um projeto que será mantido por várias pessoas
de diferentes nacionalidades e funcionam 24 horas por dia, 7 dias por semana, em escala global.
Embora o objetivo seja colocar o aplicativo em contêiner e implantá-lo no kubernetes, qualquer alteração no aplicativo fornecido que você considere necessária para atender aos critérios também será válida.
Para destacar alguns critérios, sem ordem específica:

- Organização do código
- Documentação
- Histórico de alterações
- Testes
- Mecanismos de liberação e implantação
- Segurança
- Desempenho
- Disponibilidade
- Custo
- Melhores práticas da indústria

## Requisitos

As submissões que não contiverem estes requisitos serão automaticamente desconsideradas:

1. Crie uma imagem de container com a aplicação neste repositório e publique em um repositório público (dockerhub, quay, etc);
2. Escreva todo o código que achar necessário para implantar a imagem em um cluster kubernetes;
3. Expor o aplicativo externamente ao cluster Kubernetes;
4. Configurar a aplicação para ser implantada em uma configuração altamente disponível, considerando que o cluster possui nós de trabalho em 3 zonas de disponibilidade diferentes;

## Teste

Para testar isso, use qualquer distribuição local gratuita do Kubernetes, como [minikube](https://github.com/kubernetes/minikube), [kind](https://kind.sigs.k8s.io/), [k3d] (https://k3d.io), etc.
Não há necessidade de administrar uma conta na nuvem, mesmo no nível gratuito, ou qualquer outro serviço que incorra em custos.

## Metas opcionais

Embora nem todos precisem ser implementados, quanto mais concluídos, melhor, mas também se espera que contenham qualidade de **grau de produção** e serão avaliados sob os mesmos critérios explicados acima:

- Configurar o Kubernetes para autenticação em um repositório de contêiner privado;
- Criar um script automatizando a construção e implantação de imagens;
- Adicionar um proxy reverso para rotear solicitações em vez de expor o serviço principal;
- Escrever alguns cenários de testes, sejam de desempenho, funcionais ou qualquer outro tipo de teste relevante;
- Criar um script para configurar um cluster kubernetes local, implantar a aplicação e executar os cenários de teste mencionados acima;
- Configure o cluster kubernetes local para ter mais de 2 nós de trabalho;
- Use [Helm](https://helm.sh/) em sua aplicação;
- Utilize o [Terraform](https://www.terraform.io/) para configurar o ambiente local da sua aplicação;
  - Use-o também para configurar um ambiente remoto em qualquer provedor de nuvem;

## Como executar este aplicativo

1. execute `yarn install`
2. crie um banco de dados SQL com `docker run -p 3306:3306 -e MYSQL_ROOT_PASSWORD=test -e MYSQL_DATABASE=test -e MYSQL_USER=test -e MYSQL_PASSWORD=test -d mariadb:5.5`
3. execute `yarn typeorm migração:run`
4. abra `http://localhost:3000/posts` e veja uma lista vazia
5. teste com `curl`, `postman` ou ferramentas semelhantes