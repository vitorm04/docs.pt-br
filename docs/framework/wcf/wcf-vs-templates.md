---
title: Modelos do Visual Studio do WCF
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6a608575-3535-4190-89da-911e24c8374f
caps.latest.revision: 31
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: fceb0f2ab7caa2bf3ab34ff957e3ed5f300e557c
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/30/2018
---
# <a name="wcf-visual-studio-templates"></a>Modelos do Visual Studio do WCF
[!INCLUDE[indigo1](../../../includes/indigo1-md.md)] Modelos do Visual Studio são modelos predefinidos de projeto e item, você pode usar no Visual Studio para criar rapidamente [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] ao redor de aplicativos e serviços.  
  
## <a name="using-the-wcf-templates"></a>Usando os modelos do WCF  
 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] Modelos do Visual Studio fornecem uma estrutura de classe básica para desenvolvimento de serviço. Especificamente, esses modelos fornecem as definições básicas para o contrato de serviço, contrato de dados, a implementação de serviço e configuração. Você pode usar esses modelos para criar um serviço simple com interação com o mínimo de código, bem como um bloco de construção para serviços mais avançados.  
  
### <a name="wcf-service-library-project-template"></a>Modelo de projeto de biblioteca de serviço do WCF  
 O [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] modelo de projeto de biblioteca de serviço está disponível na caixa de diálogo Novo projeto em **Visual C# \WCF** e **Basic\WCF Visual**.  
  
 Quando você cria um novo projeto usando o **serviço WCF** modelo, o novo projeto inclui automaticamente os três arquivos a seguir:  
  
-   Arquivo do contrato de serviço (Iservice1 ou IService1.vb). O arquivo do contrato de serviço é uma interface que tem [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] serviço atributos aplicados. Esse arquivo fornece a definição de um serviço simple para mostrar como definir seus serviços e inclui as operações de parâmetro e um exemplo de contrato de dados simples. Este é o arquivo padrão exibido no editor de código depois de criar um [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] projeto de serviço.  
  
-   Arquivo de implementação de serviço (Service1 ou Service1). O arquivo de implementação de serviço implementa o contrato definido no arquivo do contrato de serviço.  
  
-   Arquivo de configuração de aplicativo (App. config). O arquivo de configuração fornece os elementos básicos de um [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] modelo de serviço com uma associação HTTP seguro. Ele também inclui um ponto de extremidade para o serviço e permite a troca de metadados.  
  
> [!NOTE]
>  O Visual Studio está configurado para reconhecer o arquivo App. config como arquivo de configuração para o projeto quando ele é executado usando o [Host de serviço do WCF (WcfSvcHost.exe)](../../../docs/framework/wcf/wcf-service-host-wcfsvchost-exe.md), que é a configuração padrão. Se você hospedar a biblioteca de serviço em um executável, você precisa mover o código de configuração para o arquivo de configuração do executável, como arquivos de configuração para DLLs não são válidos.  
  
### <a name="wcf-service-application-template"></a>Modelo de aplicativo de serviço do WCF  
 O [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] modelo de aplicativo de serviço está disponível na caixa de diálogo Novo projeto em **Visual C# \WCF** e **Basic\WCF Visual**.  
  
 Quando você cria um novo projeto usando o **serviço de aplicativo Web WCF** modelo, o projeto inclui os quatro arquivos a seguir:  
  
-   Arquivo de host de serviço (service1.svc).  
  
-   Arquivo do contrato de serviço (Iservice1 ou IService1.vb).  
  
-   Arquivo de implementação de serviço (arquivo Service1.svc.cs ou Service1.svc. vb).  
  
-   Arquivo de configuração da Web (Web. config).  
  
 O modelo cria um site da Web (para ser implantado em um diretório virtual) e hospeda um serviço automaticamente.  
  
### <a name="wcf-web-site-template"></a>Modelo de Site da Web do WCF  
 O [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] modelo de Site está disponível na caixa de diálogo Novo projeto em **Visual C# \Web Site\WCF Service** e **Visual Basic\Web Site\WCF Service**. Isso cria os mesmos arquivos como o modelo de aplicativo de serviço WCF, mas organiza como se fosse um site ASP.NET. App_Code e App_Data pastas são criadas.  
  
### <a name="wcf-service-item-template"></a>Modelo de Item de serviço do WCF  
 O [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] modelo de Item de serviço é um modelo personalizado que fornece uma maneira rápida de adicionar [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] serviços para seus projetos do Visual Studio existentes.  
  
 Para usar esse modelo, vá para o **Solution Explorer** painel, clique o nome do projeto, aponte para **adicionar**e, em seguida, clique em **Novo Item** para iniciar o **adicionar novo Item** caixa de diálogo.  
  
 Os arquivos de interface e implementação de serviço são colocados na pasta raiz do projeto.  
  
 O modelo tenta mesclar a seção de configuração do novo serviço para o arquivo de configuração existente, se eles são tipos compatíveis.  
  
 Um arquivo de host de serviço (service1.svc) também é criado se o projeto existente for um projeto da Web.  
  
### <a name="wcf-wf-service-project-and-item-template"></a>Projeto de serviço do WF WCF e o modelo de Item.  
 Esses modelos criam [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] services que hospeda um serviço de fluxo de trabalho, que é um fluxo de trabalho que pode ser acessado como um serviço web. Modelos separados existem para modelos de programação imperativos ou XAML. Usar os modelos, você pode criar o fluxo de trabalho de máquina de estado ou sequencial. Para obter mais informações sobre esses tipos de fluxo de trabalho, consulte [Windows Workflow Foundation tutoriais](http://msdn.microsoft.com/library/e9705654-bd96-4b56-8d98-f1f118112d97). Para obter mais informações sobre como criar projetos de fluxo de trabalho, consulte [criar projetos de fluxo de trabalho herdado](/visualstudio/workflow-designer/creating-legacy-workflow-projects).  
  
 Designer do Visual Studio é mais ágil nas respostas quando tipo XOML fluxos de trabalho são usados em vez disso, de código com base em aqueles. Fluxo de trabalho XOML é o tipo de fluxo de trabalho padrão a ser criado.  
  
### <a name="wcf-syndication-service-library-template"></a>Modelo de biblioteca de serviço do WCF de distribuição  
 Este modelo permite que você exponha o feed no formato RSS ou ATOM como uma [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] serviço. Para obter mais informações, consulte [Sindicalização do WCF](../../../docs/framework/wcf/feature-details/wcf-syndication.md).  
  
#### <a name="changing-the-address-of-the-feed"></a>Alterar o endereço do Feed  
 O modelo de distribuição usa o Internet Explorer durante a execução. Quando você clica seu projeto no **Gerenciador de soluções** no Visual Studio, selecione **propriedades**, em seguida, selecione o **depurar** guia e você pode ver o endereço padrão das modelo. Internet Explorer tenta abrir o feed no endereço.  
  
 Se você alterar o endereço do seu feed, você deve também alterar o endereço de **depurar** guia. Se você não fizer isso, o Internet Explorer tenta abrir o feed no endereço padrão e falhar.  
  
### <a name="ajax-enabled-wcf-service-item-template"></a>Modelo de Item de serviço do WCF habilitado para AJAX  
 Este modelo expõe um controle de AJAX como uma [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] serviço. Para obter mais informações sobre controles AJAX, consulte o [documentação de controle AJAX](http://go.microsoft.com/fwlink/?LinkId=96717).  
  
### <a name="silverlight-enabled-wcf-service-item-template"></a>Modelo de Item de serviço do WCF habilitado para Silverlight  
 Este modelo cria um serviço Web que fornece dados para um cliente Silverlight ou front-end. O modelo pode ser adicionado a um projeto de aplicativo Web ou site da Web para criar um [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] serviço, que inclui o código de serviço e configuração de suporte para se comunicar com um cliente Silverlight. Você pode usar **adicionar referência de serviço** para adicionar um proxy de cliente do serviço para o cliente e trocar dados entre o cliente do Silverlight e o serviço do WCF habilitado para Silverlight.  
  
 Para acessar este modelo, clique com botão direito um projeto de aplicativo Web ou site da Web em **Solution Explorer**, clique em **adicionar um novo item**e clique em **serviço do WCF habilitado para Silverlight**.  
  
> [!NOTE]
>  O serviço do WCF habilitado para Silverlight expõe um `basicHttpBinding` ponto de extremidade sem habilitar as configurações de segurança. Portanto, as informações sobre o serviço podem ser obtidas por todos os clientes que se conectam a este serviço. Mensagens trocadas entre o serviço e o cliente também não estão assinadas ou criptografadas. Para proteger corretamente o ponto de extremidade, você deve usar a autenticação do ASP.NET, HTTPS ou outros mecanismos.  
  
## <a name="see-also"></a>Consulte também  
 [Host de serviço do WCF (WcfSvcHost.exe)](../../../docs/framework/wcf/wcf-service-host-wcfsvchost-exe.md)  
 [Cliente de teste do WCF (WcfTestClient.exe)](../../../docs/framework/wcf/wcf-test-client-wcftestclient-exe.md)
