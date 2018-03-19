---
title: "Publicação de serviço do WCF"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c806b253-cd47-4b96-b831-e73cbf08808f
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 823edadf7d387d1a509edbdf839ac6eeece5d41f
ms.sourcegitcommit: 15316053918995cc1380163a7d7e7edd5c44e6d7
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/19/2018
---
# <a name="wcf-service-publishing"></a>Publicação de serviço do WCF
[!INCLUDE[indigo1](../../../includes/indigo1-md.md)] Serviço de publicação ajuda em andamento no ambiente de desenvolvimento iniciais fornecido pelo [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] Host de serviço e [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] cliente de teste para realmente implantar o aplicativo em um ambiente de produção para fins de teste. Antes de confirmar a um plano de implantação final, você pode usar [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] serviço de publicação para verificar se seu [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] serviço executa corretamente e está pronto para ser publicado. Você também pode optar por implantar seu [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] bibliotecas em vários locais de destino para teste de serviço.  
  
## <a name="supported-services-and-target-locations"></a>Serviços com suporte e locais de destino  
 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] Serviço de publicação oferece suporte à publicação [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] serviços criados do conjunto de [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] modelos de biblioteca de serviço e seus modelos de item correspondente, que incluem o seguinte:  
  
-   [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] Modelo de biblioteca de serviço com o modelo de item.  
  
-   Biblioteca de serviço de distribuição.  
  
 Você pode encontrar esses modelos de serviço, escolhendo **arquivo** -> **novo projeto** -> **Visual Basic** ou **Visual C#**  ->  **WCF**. Para outros modelos de WCF neste local (incluindo o aplicativo de serviço de fluxo de trabalho WCF e o aplicativo de serviço WCF), você pode publicar usando [publicação para aplicativos da web com um clique](https://msdn.microsoft.com/library/dd465337\(v=vs.110\).aspx).  
  
 O serviço pode ser publicado para os seguintes locais de destino.  
  
-   IIS local.  
  
-   Sistema de arquivos.  
  
-   Site de FTP.  
  
## <a name="using-wcf-service-publishing"></a>Usando o WCF publicação de serviço  
 Execute as seguintes etapas para implantar uma implementação de serviço:  
  
1.  Abra o Visual Studio com privilégios elevados (clique com botão direito no executável e usar "Executar como administrador" para iniciá-lo).  Se você estiver usando o IIS 7.0 ou posterior, certifique-se de que você tenha instalado o componente "Metabase de IIS e compatibilidade de configuração de IIS6" usando "' em ou desativar recursos do Windows" no painel de controle.  
  
2.  Abra um projeto de serviço, selecione **criar**->**publicar \<nome do projeto >** no menu principal, ou com o botão direito no projeto no **Solution Explorer**e clique em **publicar**.  
  
3.  O **publicar** janela é exibida. Clique o **...** . botão para especificar o local de destino que o serviço deve ser implantado. Você pode selecionar para implantar o aplicativo IIS local, sistema de arquivos ou FTP Site. Se implantar o aplicativo para IIS local, você pode selecionar seu site e criar seu aplicativo da web sob ele, clicando o **criar novo aplicativo Web** ícone no canto superior direito.  
  
4.  Depois de clicar em **publicar** na janela principal do Visual Studio implanta o aplicativo para o local de destino especificado e copia os arquivos de assembly de Web. config e. svc no diretório de destino. . O nome do SVC será "ProjectName.ServiceName.svc". Depois que o serviço é publicado com êxito, você pode encontrar um hotlink na janela de saída do Visual Studio, que é semelhante a "Conectando-se ao HYPERLINK"http://localhost/WebApplicationFolderName"http://localhost/WebApplicationFolderName...". Você pode pressionar a tecla CTRL e clique no link para abrir uma página do navegador dentro do Visual Studio para exibir a estrutura de diretório de serviço.  
  
     Se você não pode navegar para o site, ele pode porque o navegador de diretório não está habilitada no IIS. Siga as dicas na seção "Coisas que você pode tentar" para habilitá-lo. Como alternativa, você pode diretamente digitar"HYPERLINK"http://localhost/WebApplicationFolderName"http://localhost/WebApplicationFolderName/ProjectName.ServiceName.svc" para exibir sua página de serviço.  
  
 Você pode usar **publicar** para especificar se deseja copiar o assembly, a configuração e o arquivo. svc para todos os serviços definidos no projeto para o local de destino e substituir arquivos existentes no destino.  
  
 Se você optar por implantar seu aplicativo no IIS local, você poderá encontrar erros relacionados à configuração do IIS. Certifique-se de que o IIS está instalado corretamente. Você pode digitar "HYPERLINK"http://localhost"http://localhost" em seu navegador e verifique se a página padrão do IIS está aparecendo.  Em alguns casos, os problemas também podem ser causados pelo ASP.NET ou [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] registro incorreto no IIS. Você pode abrir o Prompt de comando do Visual Studio e execute o comando "aspnet_regiis.exe - ir" para corrigir problemas de registro do ASP.NET ou execute o comando "ServiceModelReg.exe – ia" para corrigir problemas de registro do WCF.  
  
## <a name="files-generated-for-publishing"></a>Arquivos gerados para publicação  
 Antes de um [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] biblioteca de serviço pode ser hospedado na Web, os seguintes arquivos são gerados pela ferramenta: arquivos de assembly, o arquivo Web. config e o arquivo. svc. Todos os arquivos são copiados para o local de destino. O serviço é publicado.  
  
### <a name="assembly-files"></a>Arquivos de assembly  
 Quando você publica um [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] de serviço usando essa ferramenta, o serviço será automaticamente criado primeiro e os arquivos de assembly são gerados no projeto de serviço após a construção.  
  
### <a name="svc-file"></a>.SVC File  
 A operação de publicação gera um arquivo SVC para cada [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] serviço, se o arquivo existe ou não, para garantir a validade da versão. Há dois tipos diferentes de arquivos svc: uma para [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] biblioteca de serviço e biblioteca de serviço de distribuição e outra para sequencial e biblioteca de serviço de fluxo de trabalho de máquina de estado. Gerado \*arquivo. svc é copiado para a pasta raiz no local de destino.  
  
### <a name="webconfig-file"></a>Arquivo Web. config  
 Cada vez que um projeto de serviço é publicado em um local de destino específico, um arquivo Web. config é criado.  
  
 O arquivo Web. config gerado inclui as seções de Web que são úteis para hospedagem na Web e o conteúdo do App. config para o [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] biblioteca de serviço com as seguintes alterações:  
  
-   O endereço base foi excluído.  
  
-   Configurações de `<diagnostics>` elemento são excluídas para preservar as configurações de rastreamento da plataforma de destino.  
  
## <a name="publishing-wcf-services-with-non-http-bindings-to-iis"></a>Publicando serviços WCF com associações não HTTP no IIS  
 Se você estiver usando o IIS 7.0 ou posterior, você pode publicar [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] serviços com associações não HTTP para IIS. Você precisa fazer algumas configurações de pré-lançamento. Para obter mais informações, consulte os tópicos em [hospedagem no serviço de ativação de processos do Windows](../../../docs/framework/wcf/feature-details/hosting-in-windows-process-activation-service.md).  
  
## <a name="security"></a>Segurança  
 Publicação para IIS local requer o privilégio de administrador, porque requer o IIS em execução na conta de administrador. Se um usuário sem privilégios de administrador abrir [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] serviço de publicação, o IIS não está disponível como um local de destino. Funciona a publicação para o sistema de arquivos ou FTP Site sem privilégios de administrador.  
  
## <a name="see-also"></a>Consulte também  
 [Modelos do Visual Studio do WCF](../../../docs/framework/wcf/wcf-vs-templates.md)  
 [Host de serviço do WCF (WcfSvcHost.exe)](../../../docs/framework/wcf/wcf-service-host-wcfsvchost-exe.md)  
 [Cliente de teste do WCF (WcfTestClient.exe)](../../../docs/framework/wcf/wcf-test-client-wcftestclient-exe.md)
