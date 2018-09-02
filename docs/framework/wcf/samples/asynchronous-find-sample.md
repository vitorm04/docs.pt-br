---
title: Exemplo de assíncrono encontrado
ms.date: 03/30/2017
ms.assetid: 7a713a25-c1f4-42e1-8c4a-93d64ca45a3b
ms.openlocfilehash: 37edcb4d1f04eb56d3f24ca3acc3543d7f9696f5
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/01/2018
ms.locfileid: "43424385"
---
# <a name="asynchronous-find-sample"></a>Exemplo de assíncrono encontrado
Este exemplo mostra como usar a operação de localização assíncrona de um aplicativo cliente.  
  
## <a name="sample-details"></a>Detalhes de exemplo  
 O benefício de seguir esse padrão de design é que o cliente seja notificado de forma assíncrona dos pontos de extremidade, como resultado da solicitação de localização. Para ver como isso funciona, abra o arquivo de Client.cs. Observação o <xref:System.ServiceModel.Discovery.DiscoveryClient> objeto tem dois delegados anexados a seus manipuladores de eventos. Um delegado é chamado quando um <xref:System.ServiceModel.Discovery.DiscoveryClient.FindCompleted> é gerado e o outro é chamado sempre que um <xref:System.ServiceModel.Discovery.DiscoveryClient.FindProgressChanged> é gerado. O exemplo mostra como você pode utilizar esse padrão em seu aplicativo.  
  
> [!NOTE]
>  Este exemplo usa pontos de extremidade HTTP e para executar, o URL apropriado ACLs deve ser adicionado. Para obter mais informações, consulte [Configuring HTTP and HTTPS](../../../../docs/framework/wcf/feature-details/configuring-http-and-https.md). Executando o seguinte comando para um nível de privilégio elevado deve adicionar as ACLs apropriado. Você talvez queira substituir seu domínio e nome de usuário para os argumentos a seguir, se o comando não funcionar como está. `netsh http add urlacl url=http://+:8000/ user=%DOMAIN%\%UserName%`  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Para configurar, compilar, e executar o exemplo  
  
1.  Usando [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], abra o AsyncFind.sln.  
  
2.  Pressione CTRL+SHIFT+B para criar a solução.  
  
3.  Abra um [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] prompt de comando, navegue até o diretório \WCF\Basic\Discovery\AsyncFind\CS\service\bin\Debug ou \WCF\Basic\Discovery\AsyncFind\VB\service\bin\Debug e executar Service.exe.  
  
4.  Depois que o serviço foi iniciado, navegue até o diretório de WCF\Basic\Discovery\AsyncFind\VB\client\bin\Debug ou \WCF\Basic\Discovery\AsyncFind\CS\client\bin\Debug e execute Client.exe.  
  
5.  Observe que o cliente é capaz de localizar e chamar o serviço.  
  
> [!IMPORTANT]
>  Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e o Windows Workflow Foundation (WF) exemplos do .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos. Este exemplo está localizado no seguinte diretório.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Discovery\AsyncFind`  
  
## <a name="see-also"></a>Consulte também
