---
title: Publicação de serviço do WCF
ms.date: 03/30/2017
ms.assetid: c806b253-cd47-4b96-b831-e73cbf08808f
ms.openlocfilehash: 33725c2f393529a7e59ed0b3ae1db01a359fb9a5
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59299716"
---
# <a name="wcf-service-publishing"></a>Publicação de serviço do WCF

Publicação de serviço do Windows Communication Foundation (WCF) ajuda a está em andamento do ambiente de desenvolvimento iniciais fornecido pelo Host de serviço WCF e o cliente de teste do WCF para realmente implantar o aplicativo em um ambiente de produção para fins de teste. Antes de se comprometer com um plano de implantação final, você pode usar publicação de serviço do Windows Communication Foundation (WCF) para verificar se o seu serviço WCF executado corretamente e está pronto para ser publicado. Você também pode optar por implantar suas bibliotecas de serviço do WCF em vários locais de destino para teste.

## <a name="supported-services-and-target-locations"></a>Serviços com suporte e locais de destino

Publicação de serviço do WCF dá suporte a serviços WCF de publicação criados no conjunto de modelos de biblioteca de serviço do WCF e seus modelos de item correspondente, que incluem o seguinte:

-   Modelo WCF Service Library com modelo de item.

-   Syndication Service Library.

Você pode encontrar esses modelos de serviço, escolhendo **arquivo** > **novo projeto** > [**Visual Basic** ou **Visual C#** ] > **WCF**. Para outros modelos WCF neste local (incluindo o aplicativo de serviço de fluxo de trabalho do WCF e o aplicativo de serviço WCF), você pode publicar usando [publicação para aplicativos web com um clique](https://docs.microsoft.com/previous-versions/aspnet/dd465337(v=vs.110)).

O serviço pode ser publicado para os seguintes locais de destino.

-   IIS local.

-   Sistema de arquivos.

-   Site de FTP.

## <a name="using-wcf-service-publishing"></a>Usando o WCF publicação de serviço

Execute as seguintes etapas para implantar uma implementação de serviço:

1. Abra o Visual Studio com privilégios elevados (clique com botão direito no executável e escolha **executar como administrador** para abri-lo).  Se você estiver usando o IIS 7.0 ou posterior, certifique-se de que você instalou o componente de "Metabase de IIS e compatibilidade de configuração de IIS6" usa "Windows ativar ou desativar recursos do" no painel de controle.

2. Abra um projeto de serviço, selecione **construir** > **publicar \<nome do projeto >** no menu principal, ou clique com botão direito no projeto no **Solution Explorer**e clique em **publicar**.

3. O **publicar** janela é exibida. Clique o **...** . botão para especificar o local de destino que o serviço deve ser implantado. Você pode selecionar para implantar o aplicativo no IIS local, sistema de arquivos ou FTP Site. Se implantar o aplicativo IIS local, você pode selecionar seu site e crie seu aplicativo web sob ele, clicando o **criar novo aplicativo Web** ícone no canto superior direito.

4. Depois de clicar em **publicar** na janela principal, o Visual Studio implanta o aplicativo para o local de destino especificado e copia os arquivos Web. config,. svc e assembly para o diretório de destino. . O nome de. svc será "ProjectName.ServiceName.svc". Depois que o serviço é publicado com êxito, você pode encontrar um hotlink na janela de saída do Visual Studio, que é semelhante a "conectar-se ao `http://localhost/WebApplicationFolderName...`". Você pode pressionar a tecla CTRL e clique no link para abrir uma página do navegador dentro do Visual Studio para exibir a estrutura de diretório de serviço.

     Se você não pode navegar para o site, talvez seja porque o navegador de diretório não está habilitado no IIS. Siga as dicas na seção "Coisas que você pode tentar" para habilitá-lo. Como alternativa, você pode digitar diretamente `http://localhost/WebApplicationFolderName/ProjectName.ServiceName.svc` para exibir sua página de serviço.

Você pode usar **publicar** para especificar se deseja copiar o assembly, a configuração e o arquivo. svc para todos os serviços definidos no projeto para o local de destino e, em seguida, substituir arquivos existentes no destino.

Se você optar por implantar seu aplicativo no IIS local, você poderá encontrar erros relacionados à configuração do IIS. Certifique-se de que o IIS está instalado corretamente. Você pode inserir `http://localhost` na barra de endereços de seu navegador e verifique se a página padrão do IIS exibe. Em alguns casos, os problemas também podem ser causados por registro incorreto de ASP.NET ou WCF no IIS. Você pode abrir o Prompt de comando do desenvolvedor para Visual Studio e execute o comando `aspnet_regiis.exe -ir` para corrigir problemas de registro do ASP.NET, ou execute o comando `ServiceModelReg.exe –ia` para corrigir problemas de registro do WCF.

## <a name="files-generated-for-publishing"></a>Arquivos gerados para publicação
 Antes de uma biblioteca de serviços WCF pode ser hospedados na Web, os seguintes arquivos são gerados pela ferramenta: arquivos de assembly, o arquivo Web. config e o arquivo. svc. Todos os arquivos são copiados para o local de destino. O serviço, em seguida, é publicado.

### <a name="assembly-files"></a>Arquivos de assembly
 Quando você publica um serviço WCF usando essa ferramenta, o serviço será automaticamente criado primeiro e os arquivos de assembly são gerados no projeto de serviço depois de criar.

### <a name="svc-file"></a>. Arquivo SVC
 A operação de publicação gera um arquivo *. svc para cada serviço WCF, se o arquivo existe ou não, para assegurar a validade de versão. Há dois tipos diferentes de arquivos svc: um para o WCF Service Library e Syndication Service Library e outra para Sequential e State Machine Workflow Service Library. Gerado \*arquivo. svc é copiado para a pasta raiz no local de destino.

### <a name="webconfig-file"></a>Web.config File
 Cada vez que um projeto de serviço é publicado em um local de destino específico, um arquivo Web. config é criado.

 O arquivo Web. config gerado inclui as seções de Web que são úteis para hospedagem na Web e o conteúdo do App. config para o WCF service library com as seguintes alterações:

-   O endereço básico é excluído.

-   As configurações no `<diagnostics>` elemento são excluídas para preservar as configurações de rastreamento da plataforma de destino.

## <a name="publishing-wcf-services-with-non-http-bindings-to-iis"></a>Publicar os serviços WCF com associações não HTTP no IIS
 Se você estiver usando IIS7.0 ou posterior, você pode publicar os serviços WCF com associações não HTTP ao IIS. Você precisa fazer algumas configurações de pré-lançamento. Para obter mais informações, consulte os tópicos em [hospedagem no serviço de ativação de processos do Windows](../../../docs/framework/wcf/feature-details/hosting-in-windows-process-activation-service.md).

## <a name="security"></a>Segurança
 Publicação no IIS local exige privilégio de administrador, porque requer o IIS em execução na conta de administrador. Se um usuário sem privilégios de administrador é aberta a publicação de serviço do WCF, o IIS não está disponível como um local de destino. Publicação no sistema de arquivos ou o FTP Site funciona sem privilégio de administrador.

## <a name="see-also"></a>Consulte também

- [Modelos do Visual Studio do WCF](../../../docs/framework/wcf/wcf-vs-templates.md)
- [Host de serviço do WCF (WcfSvcHost.exe)](../../../docs/framework/wcf/wcf-service-host-wcfsvchost-exe.md)
- [Cliente de teste do WCF (WcfTestClient.exe)](../../../docs/framework/wcf/wcf-test-client-wcftestclient-exe.md)