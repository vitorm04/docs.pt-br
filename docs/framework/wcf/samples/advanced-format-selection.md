---
title: Seleção de formato avançada
ms.date: 03/30/2017
ms.assetid: e02d9082-4d55-41d8-9329-98f6d1c77f06
ms.openlocfilehash: e5c396ce22e9021d453a70f3826b0bd3cc6aaf42
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44082207"
---
# <a name="advanced-format-selection"></a>Seleção de formato avançada
Este exemplo demonstra como estender o modelo de programação REST do Windows Communication Foundation (WCF) para dar suporte a novos formatos de resposta de saída. Além disso, o exemplo usa um modelo T4 para retornar a resposta como uma página XHTML, demonstrando como um modelo de programação de estilo de exibição pode ser implementado.  
  
## <a name="sample-details"></a>Detalhes de exemplo  
 O exemplo consiste em um serviço simples, juntamente com o código do cliente que faz solicitações para o serviço.  O serviço dá suporte a uma única operação de [WebGet], que tem a seguinte assinatura de método: `Message EchoListWithGet(string list);`  
  
 Quando o cliente faz uma solicitação para o serviço, ele fornece uma lista separada por vírgulas de itens do `list` parâmetro de cadeia de caracteres de consulta e o serviço retorna essa mesma lista em um dos seguintes formatos: XML, JSON, Atom, XHTML ou jpeg.  
  
 O formato da resposta retornado pelo serviço é determinado primeiro por um `format` parâmetro de cadeia de caracteres de consulta e segundo por um cabeçalho HTTP aceitar fornecido com a solicitação. Se o valor de `format` parâmetro de cadeia de caracteres de consulta é um dos formatos anteriores e, em seguida, a resposta é retornada no formato. Se o `format` cadeia de caracteres de consulta não estiver presente, então o serviço itera através dos elementos de cabeçalho Accept da solicitação e retorna o formato do primeiro tipo de conteúdo compatível com o serviço.  
  
 O tipo de retorno da operação é digno de nota. O só nativamente o modelo de programação REST do WCF dá suporte a formatos de resposta XML e JSON quando uma operação retorna um tipo diferente de <xref:System.ServiceModel.Channels.Message>. No entanto, ao usar <xref:System.ServiceModel.Channels.Message> como o tipo de retorno, o desenvolvedor tem controle completo sobre como o conteúdo da mensagem deve ser formatado.  
  
 O exemplo usa o <xref:System.ServiceModel.Web.WebOperationContext.CreateXmlResponse%2A>, <xref:System.ServiceModel.Web.WebOperationContext.CreateJsonResponse%2A> e <xref:System.ServiceModel.Web.WebOperationContext.CreateAtom10Response%2A> métodos para serializar a lista de cadeias de caracteres em mensagens XML, JSON e ATOM, respectivamente. Para o formato de resposta de jpeg, o <xref:System.ServiceModel.Web.WebOperationContext.CreateStreamResponse%2A> método é usado e a imagem é salva no fluxo. Para a resposta XHTML, o <xref:System.ServiceModel.Web.WebOperationContext.CreateTextResponse%2A> for usada junto com um modelo T4 pré-processado, que consiste em um arquivo. TT e um arquivo. cs do gerado automaticamente. O arquivo. TT permite que um desenvolvedor escreva uma resposta em um formulário de modelo que contém variáveis e estruturas de controle. Para obter mais informações sobre T4, consulte [gerando artefatos por usando modelos de texto](https://go.microsoft.com/fwlink/?LinkId=166023).  
  
 O exemplo consiste em um serviço auto-hospedado e um cliente que é executado dentro de um aplicativo de console. Como o aplicativo de console é executado, o cliente faz solicitações para o serviço e grava as informações pertinentes das respostas à janela do console.  
  
#### <a name="to-run-this-sample"></a>Para executar este exemplo  
  
1.  Abra a solução para o exemplo de seleção de formato avançada. Ao iniciar [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], você deve executar como administrador para o exemplo para executar com êxito. Fazer isso clicando com o [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] ícone e escolhendo **executar como administrador** no menu de contexto.  
  
2.  Pressione CTRL + SHIFT + B para compilar a solução e, em seguida, pressione Ctrl-F5 para executar o projeto de AdvancedFormatSelection do aplicativo de console sem depuração. A janela do console é exibida e fornece o URI do serviço em execução e o URI do HTML na página para a execução do serviço de Ajuda.  
  
3.  Como o exemplo é executado, o cliente envia solicitações ao serviço e grava as respostas para a janela do console. Observe os diferentes formatos das respostas: XML, JSON, Atom e XHTML.  
  
4.  Você precisará, em seguida, navegue até um URI no qual você pode solicitar a resposta em um formato JPEG. Abra um navegador e navegue até um determinado URI.  
  
5.  Pressione qualquer tecla para encerrar a amostra.  
  
> [!IMPORTANT]
>  Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e o Windows Workflow Foundation (WF) exemplos do .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos. Este exemplo está localizado no seguinte diretório.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Web\AdvancedFormatSelection`  
  
## <a name="see-also"></a>Consulte também
