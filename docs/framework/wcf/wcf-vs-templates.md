---
title: Modelos do Visual Studio do WCF
ms.date: 03/30/2017
ms.assetid: 6a608575-3535-4190-89da-911e24c8374f
ms.openlocfilehash: 13183ad5f05350c34eebd025eca3faa7d97644f8
ms.sourcegitcommit: d9470d8b2278b33108332c05224d86049cb9484b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/17/2020
ms.locfileid: "81608017"
---
# <a name="wcf-visual-studio-templates"></a>Modelos do Visual Studio do WCF
Os modelos do Windows Communication Foundation (WCF) Visual Studio são modelos de projeto e itens predefinidos que você pode usar no Visual Studio para criar rapidamente serviços WCF e aplicativos ao redor.  
  
## <a name="using-the-wcf-templates"></a>Usando os modelos WCF  
 Os modelos do WCF Visual Studio fornecem uma estrutura básica de classe para o desenvolvimento de serviços. Especificamente, esses modelos fornecem as definições básicas para contrato de serviço, contrato de dados, implementação de serviços e configuração. Você pode usar esses modelos para criar um serviço simples com interação mínima de código, bem como um bloco de construção para serviços mais avançados.  
  
### <a name="wcf-service-library-project-template"></a>Modelo de projeto da biblioteca de serviços do WCF  
 O modelo de projeto da Biblioteca de Serviços wcf está disponível na nova caixa de diálogo do projeto em **Visual C#\WCF** e **Visual Basic\WCF**.  
  
 Quando você cria um novo projeto usando o modelo **wcf service,** o novo projeto inclui automaticamente os três arquivos a seguir:  
  
- Arquivo de contrato de serviço (IService1.cs ou IService1.vb). O arquivo de contrato de serviço é uma interface que tem atributos de serviço WCF aplicados. Este arquivo fornece uma definição de um serviço simples para mostrar como definir seus serviços e inclui operações baseadas em parâmetros e uma amostra simples de contrato de dados. Este é o arquivo padrão exibido no editor de código depois de criar um projeto de serviço WCF.  
  
- Arquivo de implementação de serviço (Service1.cs ou Service1.vb). O arquivo de implementação do serviço implementa o contrato definido no arquivo do contrato de serviço.  
  
- Arquivo de configuração do aplicativo (App.config). O arquivo de configuração fornece os elementos básicos de um modelo de serviço WCF com uma vinculação HTTP segura. Ele também inclui um ponto final para o serviço e permite a troca de metadados.  
  
> [!NOTE]
> O Visual Studio está configurado para reconhecer o arquivo App.config como o arquivo de configuração do projeto quando ele é executado usando o [WCF Service Host (WcfSvcHost.exe),](wcf-service-host-wcfsvchost-exe.md)que é a configuração padrão. Se você hospedar a biblioteca de serviços em um executável, você terá que mover o código de configuração para o arquivo de configuração do executável, pois os arquivos de configuração para DLLs não são válidos.  
  
### <a name="wcf-service-application-template"></a>Modelo de aplicativo de serviço WCF  
 O modelo de aplicativo de serviço WCF está disponível na caixa de diálogo Novo Projeto em **Visual C#\WCF** e **Visual Basic\WCF**.  
  
 Quando você cria um novo projeto usando o modelo **wcf web application service,** o projeto inclui os quatro arquivos a seguir:  
  
- Arquivo host de serviço (service1.svc).  
  
- Arquivo de contrato de serviço (IService1.cs ou IService1.vb).  
  
- Arquivo de implementação de serviço (Service1.svc.cs ou Service1.svc.vb).  
  
- Arquivo de configuração web (Web.config).  
  
 O modelo cria automaticamente um site da Web (a ser implantado em um diretório virtual) e hospeda um serviço nele.  
  
### <a name="wcf-web-site-template"></a>Modelo de site da WCF  
 O modelo do Site do WCF está disponível na caixa de diálogo Novo Projeto em **Visual C#\Web Site\WCF Service** and **Visual Basic\Web Site\WCF Service**. Isso cria os mesmos arquivos do modelo wcf service application, mas organiza-o como se fosse um ASP.NET site. pastas App_Code e App_Data são criadas.  
  
### <a name="wcf-service-item-template"></a>Modelo de item de serviço WCF  
 O modelo wcf service item é um modelo personalizado que fornece uma maneira rápida de adicionar serviços WCF aos seus projetos existentes do Visual Studio.  
  
 Para usar este modelo, vá para o painel **Solution Explorer,** clique com o botão direito do mouse no nome do projeto, **aponte**para Adicionar e clique **em Novo Item** para iniciar a caixa de diálogo **Adicionar novo item.**  
  
 Os arquivos de interface de serviço e implementação são colocados na pasta de projeto raiz.  
  
 O modelo tenta mesclar a seção de configuração do novo serviço ao arquivo de configuração existente, se eles forem tipos compatíveis.  
  
 Um arquivo host de serviço (service1.svc) também é criado se o projeto existente for um projeto Web.  
  
### <a name="wcf-wf-service-project-and-item-template"></a>WCF WF Service Project e Item Template.  
 Esses modelos criam serviços WCF que hospedam um Serviço de Fluxo de Trabalho, que é um fluxo de trabalho que pode ser acessado como um serviço web. Existem modelos separados para modelos de programação XAML ou imperativos. Usando os modelos, você pode criar fluxo de trabalho seqüencial ou de máquina estatal. Para obter mais informações sobre esses tipos de fluxo de trabalho, consulte [Como: Criar um fluxo de trabalho](../windows-workflow-foundation/how-to-create-a-workflow.md). Para obter mais informações sobre a criação de projetos de fluxo de trabalho, consulte [Criando projetos de fluxo de trabalho legados](/visualstudio/workflow-designer/developing-applications-with-the-workflow-designer).  
  
 O designer visual studio é mais responsivo quando os fluxos de trabalho do tipo XOML são usados em vez dos baseados em código. O fluxo de trabalho XOML é o tipo padrão de fluxo de trabalho a ser criado.  
  
### <a name="wcf-syndication-service-library-template"></a>Modelo de biblioteca de serviços de sindicância WCF  
 Este modelo permite que você exponha seu feed no formato RSS ou ATOM como um serviço WCF. Para obter mais informações, consulte [WCF Syndication](./feature-details/wcf-syndication.md).  
  
#### <a name="changing-the-address-of-the-feed"></a>Alterando o endereço da alimentação  
 O modelo de sindicância usa o Internet Explorer durante a execução. Ao clicar com o botão direito do mouse no projeto no **Solutions Explorer** no Visual Studio, selecione **Propriedades,** selecione a guia **Depuração** e verá o endereço padrão do modelo. O Internet Explorer tenta abrir o feed neste endereço.  
  
 Se você alterar o endereço do seu feed, você também deve alterar o endereço na guia **Depuração.** Se você não fizer isso, o Internet Explorer tentará abrir o feed no endereço padrão e falhar.  
  
### <a name="ajax-enabled-wcf-service-item-template"></a>Modelo de item de serviço WCF habilitado para AJAX  
 Este modelo expõe um controle AJAX como um serviço WCF. Para obter mais informações sobre os controles AJAX, consulte [a documentação de controle AJAX](/aspnet/ajax/).  
  
### <a name="silverlight-enabled-wcf-service-item-template"></a>Modelo de item de serviço WCF habilitado para Silverlight  
 Este modelo cria um serviço web que fornece dados para um cliente Silverlight ou front-end. O modelo pode ser adicionado a um site ou projeto de aplicativo da Web para criar um serviço WCF, que inclui código de serviço e configuração que suportam a comunicação com um cliente Silverlight. Em seguida, você pode usar **adicionar referência de serviço** para adicionar um proxy cliente do serviço ao cliente e trocar dados entre o cliente Silverlight e o serviço WCF habilitado para Silverlight.  
  
 Para acessar este modelo, clique com o botão direito do mouse em um site ou projeto de aplicativo da Web no **Solution Explorer,** clique em **Adicionar um novo item**e clique em **Silverlight-enabled WCF Service**.  
  
> [!NOTE]
> O Serviço WCF habilitado para `basicHttpBinding` Silverlight expõe um ponto final sem ativar nenhuma configuração de segurança. Portanto, informações sobre o serviço podem ser obtidas por todos os clientes que se conectam a esse serviço. As mensagens trocadas entre o serviço e o cliente também não são assinadas ou criptografadas. Para proteger o ponto final corretamente, você deve usar ASP.NET autenticação, HTTPS ou outros mecanismos.  
  
## <a name="see-also"></a>Confira também

- [Host de serviço do WCF (WcfSvcHost.exe)](wcf-service-host-wcfsvchost-exe.md)
- [Cliente de Teste do WCF (WcfTestClient.exe)](wcf-test-client-wcftestclient-exe.md)
