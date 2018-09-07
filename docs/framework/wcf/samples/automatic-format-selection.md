---
title: Seleção automática de formato
ms.date: 03/30/2017
ms.assetid: dab51e56-8517-4a6a-bb54-b55b15ab37bb
ms.openlocfilehash: 4fd695195f5c7c13bc088248a6b3c12388328d37
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44084021"
---
# <a name="automatic-format-selection"></a>Seleção automática de formato
Este exemplo demonstra como habilitar a seleção automática de formato (JSON ou XML) com o modelo, bem como definir explicitamente o formato no código da operação de programação REST do Windows Communication Foundation (WCF).  
  
## <a name="sample-details"></a>Detalhes de exemplo  
 O exemplo consiste em um serviço juntamente com o código do cliente que faz solicitações para o serviço. O serviço oferece suporte a um único HTTP `GET` operação (`EchoWithGet`) e um único HTTP `POST` operação (`EchoWithPost`). Ambas as operações esperam uma cadeia de caracteres e, em seguida, retornam a cadeia de caracteres na resposta. Com o `GET` operação, a cadeia de caracteres é fornecida em um parâmetro de cadeia de caracteres de consulta do URI. Com o `POST` operação, a cadeia de caracteres é fornecida no corpo da solicitação, serializado em XML. O serviço é capaz de retornar respostas em XML ou JSON, utilizando a nova seleção automática de formato e os recursos de seleção de formato imperativa no [!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)].  
  
 No exemplo, a seleção automática de formato é habilitada usando o arquivo App. config. No ponto de extremidade de HTTP da Web padrão, o `automaticFormatSelectionEnabled` atributo tem um valor de `true`. Com a seleção automática de formato habilitada, a infraestrutura do WCF seleciona o formato mais apropriado resposta (XML ou JSON) considerando os cabeçalhos de aceitação HTTP ou o tipo de conteúdo da solicitação. O desenvolvedor não é necessário para fornecer qualquer configuração diferente de configuração ou código adicional a `automaticFormatSelectionEnabled` atributo `true` para usar esse novo recurso. No código do cliente em Program.cs, as solicitações são enviadas para ambos os `GET` e `POST` operações do serviço com o cabeçalho HTTP aceitar especificado como "application/xml" ou "application/json" e o serviço retorna uma resposta em que formato respectivo.  
  
 Além disso, no `GET` operação, a seleção de formato obrigatório é usada. O `GET` operação verifica se há um recurso opcional `format` parâmetro de cadeia de caracteres de consulta e se estiver presente, define o formato da resposta no <xref:System.ServiceModel.Web.WebOperationContext.OutgoingResponse%2A> propriedade. Imperativamente definir o formato da resposta dessa maneira substitui a seleção automática de formato feita pela infraestrutura do WCF.  
  
 O exemplo consiste em um serviço auto-hospedado e um cliente que é executado dentro de um aplicativo de console. Como o aplicativo de console é executado, o cliente faz solicitações para o serviço e grava as informações pertinentes das respostas à janela do console.  
  
#### <a name="to-use-this-sample"></a>Para usar este exemplo  
  
1.  Abra a solução do exemplo de seleção de formato automática. Ao iniciar [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], você deve executar como administrador para o exemplo para executar com êxito. Fazer isso clicando com o [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] ícone e selecione **executar como administrador** no menu de contexto.  
  
2.  Pressione CTRL + SHIFT + B para compilar a solução e, em seguida, pressione Ctrl + F5 para executar o projeto de AutomaticFormatSelection do aplicativo de console. A janela do console é exibida e fornece o URI do serviço em execução e o URI do HTML na página para a execução do serviço de Ajuda.  
  
3.  Como o exemplo é executado, o cliente envia solicitações ao serviço e grava as respostas para a janela do console. Observe os diferentes formatos das respostas em XML e JSON.  
  
4.  Pressione qualquer tecla para encerrar a amostra.  
  
> [!IMPORTANT]
>  Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e o Windows Workflow Foundation (WF) exemplos do .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos. Este exemplo está localizado no seguinte diretório.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Web\AutomaticFormatSelection`  
  
## <a name="see-also"></a>Consulte também
