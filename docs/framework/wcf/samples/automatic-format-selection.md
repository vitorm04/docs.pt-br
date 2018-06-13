---
title: Seleção automática de formato
ms.date: 03/30/2017
ms.assetid: dab51e56-8517-4a6a-bb54-b55b15ab37bb
ms.openlocfilehash: 8c26253bee069bf9bbc009ea219e6c12cab034ef
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33803940"
---
# <a name="automatic-format-selection"></a>Seleção automática de formato
Este exemplo demonstra como habilitar a seleção automática de formato (XML ou JSON) com o restante do Windows Communication Foundation (WCF) programação de modelo, bem como definir o formato explicitamente no código da operação.  
  
## <a name="sample-details"></a>Detalhes de exemplo  
 O exemplo consiste em um serviço junto com o código do cliente que faz solicitações para o serviço. O serviço oferece suporte a um único HTTP `GET` operação (`EchoWithGet`) e um único HTTP `POST` operação (`EchoWithPost`). As duas operações esperam uma cadeia de caracteres e, em seguida, retornam a cadeia de caracteres na resposta. Com o `GET` operação, a cadeia de caracteres é fornecida em um parâmetro de cadeia de caracteres de consulta do URI. Com o `POST` operação, a cadeia de caracteres é fornecida no corpo da solicitação, serializado em XML. O serviço é capaz de retornar respostas em XML ou JSON, usando a nova seleção automática de formato e recursos de seleção de formato obrigatório no [!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)].  
  
 No exemplo, a seleção automática de formato é habilitada usando o arquivo App. config. No ponto de extremidade de Web HTTP padrão, o `automaticFormatSelectionEnabled` atributo tem um valor de `true`. Seleção automática de formato habilitada, a infraestrutura WCF seleciona o mais apropriado formato da resposta (XML ou JSON) considerando os cabeçalhos HTTP aceitar ou tipo de conteúdo da solicitação. O desenvolvedor não precisa fornecer qualquer configuração diferente de configuração ou código adicional a `automaticFormatSelectionEnabled` atributo `true` para usar esse novo recurso. No código do cliente em Program.cs, solicitações são enviadas para o `GET` e `POST` operações do serviço com o cabeçalho aceitar HTTP especificado como "application/xml" ou "application/json" e o serviço retorna uma resposta em que formato do respectivo.  
  
 Também no `GET` operação, a seleção de formato obrigatório é usada. O `GET` operação verifica opcional `format` parâmetro de cadeia de caracteres de consulta e, se presente, define o formato da resposta no <xref:System.ServiceModel.Web.WebOperationContext.OutgoingResponse%2A> propriedade. Imperativa definindo o formato da resposta dessa maneira substitui a seleção automática de formato feita pela infraestrutura do WCF.  
  
 O exemplo consiste em um serviço auto-hospedado e um cliente que é executado dentro de um aplicativo de console. Como o aplicativo de console é executado, o cliente faz solicitações para o serviço e grava as informações pertinentes entre as respostas para a janela do console.  
  
#### <a name="to-use-this-sample"></a>Para usar este exemplo  
  
1.  Abra a solução do exemplo de seleção de formato automática. Ao iniciar [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], você deve executar como administrador para o exemplo para executar com êxito. Fazer isso clicando com o [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] ícone e selecione **executar como administrador** no menu de contexto.  
  
2.  Pressione CTRL + SHIFT + B para compilar a solução e, em seguida, pressione Ctrl + F5 para executar o projeto de AutomaticFormatSelection do aplicativo de console. A janela do console é exibida e fornece o URI do serviço em execução e o URI do HTML ajuda a página para o serviço em execução.  
  
3.  Como o exemplo é executado, o cliente envia solicitações ao serviço e grava as respostas para a janela do console. Observe os diferentes formatos de respostas em XML e JSON.  
  
4.  Pressione qualquer tecla para encerrar o exemplo.  
  
> [!IMPORTANT]
>  Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos do Windows Workflow Foundation (WF) para o .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos. Este exemplo está localizado no seguinte diretório.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Web\AutomaticFormatSelection`  
  
## <a name="see-also"></a>Consulte também
