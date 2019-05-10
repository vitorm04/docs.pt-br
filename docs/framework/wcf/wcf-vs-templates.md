---
title: Modelos do Visual Studio do WCF
ms.date: 03/30/2017
ms.assetid: 6a608575-3535-4190-89da-911e24c8374f
ms.openlocfilehash: 2e192e671d37e096e4199b295d4f533194ab89b6
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64613228"
---
# <a name="wcf-visual-studio-templates"></a>Modelos do Visual Studio do WCF
Modelos do Visual Studio Windows Communication Foundation (WCF) são predefinidos de projeto e modelos de item, que você pode usar no Visual Studio para criar rapidamente os serviços WCF e aplicativos ao redor.  
  
## <a name="using-the-wcf-templates"></a>Usando os modelos do WCF  
 Modelos do Visual Studio do WCF fornecem uma estrutura de classe básica para o desenvolvimento de serviço. Especificamente, esses modelos fornecem as definições básicas para o contrato de serviço, contrato de dados, implementação de serviço e configuração. Você pode usar esses modelos para criar um serviço simple com interação mínima de código, bem como um bloco de construção para os serviços mais avançados.  
  
### <a name="wcf-service-library-project-template"></a>Modelo de projeto de biblioteca de serviço do WCF  
 O modelo de projeto de biblioteca de serviço WCF está disponível na caixa de diálogo Novo projeto sob **Visual C# \WCF** e **Basic\WCF Visual**.  
  
 Quando você cria um novo projeto usando o **serviço do WCF** modelo, o novo projeto inclui automaticamente os três arquivos a seguir:  
  
- Arquivo do contrato de serviço (arquivo IService1.cs ou IService1.vb). O arquivo do contrato de serviço é uma interface que tem os atributos de serviço WCF aplicados. Esse arquivo fornece uma definição de um serviço simples para mostrar a você como definir os serviços e inclui as operações com base no parâmetro e um exemplo de contrato de dados simples. Este é o arquivo padrão exibido no editor de código depois de criar um projeto de serviço do WCF.  
  
- Arquivo de implementação de serviço (Service1.cs or Service1.vb). O arquivo de implementação de serviço implementa o contrato definido no arquivo do contrato de serviço.  
  
- Arquivo de configuração de aplicativo (App. config). O arquivo de configuração fornece os elementos básicos de um modelo de serviço WCF com uma associação HTTP segura. Ele também inclui um ponto de extremidade para o serviço e permite a troca de metadados.  
  
> [!NOTE]
>  Visual Studio estiver configurado para reconhecer o arquivo App. config como o arquivo de configuração para o projeto quando ele é executado usando o [Host de serviço do WCF (WcfSvcHost.exe)](../../../docs/framework/wcf/wcf-service-host-wcfsvchost-exe.md), que é a configuração padrão. Se você hospedar a biblioteca de serviço em um executável, você precisa mover o código de configuração para o arquivo de configuração do executável, como arquivos de configuração para DLLs não são válidos.  
  
### <a name="wcf-service-application-template"></a>Modelo de aplicativo de serviço do WCF  
 O modelo de aplicativo de serviço WCF está disponível na caixa de diálogo Novo projeto em **Visual C# \WCF** e **Basic\WCF Visual**.  
  
 Quando você cria um novo projeto usando o **serviço de aplicativo Web WCF** modelo, o projeto inclui os seguintes quatro arquivos:  
  
- Arquivo de host de serviço (service1.svc).  
  
- Arquivo do contrato de serviço (arquivo IService1.cs ou IService1.vb).  
  
- Arquivo de implementação de serviço (arquivo Service1.svc.cs ou Service1.svc.vb).  
  
- Arquivo de configuração da Web (Web. config).  
  
 O modelo cria um site da Web (para ser implantado em um diretório virtual) e hospeda um serviço nele automaticamente.  
  
### <a name="wcf-web-site-template"></a>Modelo de Site da Web do WCF  
 O modelo de Site de Web do WCF está disponível na caixa de diálogo Novo projeto em **Visual C# \Web Site\WCF Service** e **Visual Basic\Web Site\WCF Service**. Isso cria os mesmos arquivos que o modelo de aplicativo de serviço WCF, mas organiza como se fosse um site do ASP.NET. App_Code e App_Data pastas são criadas.  
  
### <a name="wcf-service-item-template"></a>Modelo de Item de serviço do WCF  
 O modelo de Item de serviço do WCF é um modelo personalizado que fornece uma maneira rápida para adicionar os serviços WCF para seus projetos existentes do Visual Studio.  
  
 Para usar esse modelo, vá para o **Gerenciador de soluções** painel, clique com botão direito no nome do projeto, aponte para **Add**e, em seguida, clique em **Novo Item** para iniciar o **adicionar novo Item** caixa de diálogo.  
  
 Os arquivos de interface e implementação de serviço são colocados na pasta raiz do projeto.  
  
 O modelo tenta mesclar a seção de configuração do novo serviço para o arquivo de configuração existente, se eles forem tipos compatíveis.  
  
 Um arquivo de host de serviço (service1.svc) também é criado se o projeto existente é um projeto Web.  
  
### <a name="wcf-wf-service-project-and-item-template"></a>Projeto de serviço do WF WCF e o modelo de Item.  
 Esses modelos criam serviços WCF que hospedam um serviço de fluxo de trabalho, que é um fluxo de trabalho que pode ser acessado como um serviço web. Existem modelos separados para XAML ou modelos de programação imperativos. Usando os modelos, você pode criar o fluxo de trabalho sequenciais ou de estado de máquina. Para obter mais informações sobre esses tipos de fluxo de trabalho, consulte [como: Criar um fluxo de trabalho](../windows-workflow-foundation/how-to-create-a-workflow.md). Para obter mais informações sobre como criar projetos de fluxo de trabalho, consulte [Criando projetos herdados de fluxo de trabalho](/visualstudio/workflow-designer/creating-legacy-workflow-projects).  
  
 Designer do Visual Studio é mais responsivo ao tipo XOML fluxos de trabalho são usados em vez disso, de código com base aqueles. Fluxo de trabalho XOML é o tipo de fluxo de trabalho padrão a ser criado.  
  
### <a name="wcf-syndication-service-library-template"></a>Modelo de biblioteca de serviço de Sindicalização do WCF  
 Este modelo permite que você exponha o seu feed no formato RSS ou ATOM como um serviço WCF. Para obter mais informações, consulte [Sindicalização do WCF](../../../docs/framework/wcf/feature-details/wcf-syndication.md).  
  
#### <a name="changing-the-address-of-the-feed"></a>Alterando o endereço do Feed  
 O modelo de sindicalização usa o Internet Explorer durante a execução. Quando você clique em seu projeto no **Gerenciador de soluções** no Visual Studio, selecione **propriedades**, em seguida, selecione o **depurar** guia e você pode ver o endereço padrão das modelo. Internet Explorer tenta abrir o feed nesse endereço.  
  
 Se você alterar o endereço do seu feed, você também deve alterar o endereço na **depurar** guia. Se você não fizer isso, o Internet Explorer tenta abrir o feed no endereço padrão e falhar.  
  
### <a name="ajax-enabled-wcf-service-item-template"></a>Modelo de Item de serviço do WCF habilitado para AJAX  
 Este modelo apresenta um controle AJAX como um serviço WCF. Para obter mais informações sobre controles do AJAX, consulte o [documentação de controle AJAX](https://go.microsoft.com/fwlink/?LinkId=96717).  
  
### <a name="silverlight-enabled-wcf-service-item-template"></a>Modelo de Item de serviço do WCF habilitado para Silverlight  
 Este modelo cria um serviço Web que fornece dados para um cliente do Silverlight ou front-end. O modelo pode ser adicionado a um projeto de aplicativo Web ou site da Web para criar um serviço WCF, que inclui o código de serviço e a configuração que dão suporte à comunicação com um cliente do Silverlight. Você pode usar **adicionar referência de serviço** para adicionar um proxy do cliente do serviço ao cliente e trocar dados entre o cliente do Silverlight e o serviço WCF habilitado para Silverlight.  
  
 Para acessar esse modelo, clique com botão direito a um projeto de aplicativo Web ou site da Web no **Gerenciador de soluções**, clique em **adicionar um novo item**e clique em **serviço WCF habilitado para Silverlight**.  
  
> [!NOTE]
>  O serviço do WCF habilitado para Silverlight expõe um `basicHttpBinding` ponto de extremidade sem habilitar quaisquer configurações de segurança. Portanto, as informações sobre o serviço podem ser obtidas por todos os clientes que se conectam a este serviço. Mensagens trocadas entre o serviço e o cliente também não estão assinadas ou criptografadas. Para proteger corretamente o ponto de extremidade, você deve usar a autenticação do ASP.NET, HTTPS ou outros mecanismos.  
  
## <a name="see-also"></a>Consulte também

- [Host de serviço do WCF (WcfSvcHost.exe)](../../../docs/framework/wcf/wcf-service-host-wcfsvchost-exe.md)
- [Cliente de teste do WCF (WcfTestClient.exe)](../../../docs/framework/wcf/wcf-test-client-wcftestclient-exe.md)
