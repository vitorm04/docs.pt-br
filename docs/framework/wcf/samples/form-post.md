---
title: Postagem de formulário
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fa6f84f9-2e07-4e3c-92d0-a245308b7dff
caps.latest.revision: 9
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 31d2ebbdb6f899390d7b3af485c1583fb80ae6dc
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/30/2018
---
# <a name="form-post"></a>Postagem de formulário
Este exemplo demonstra como estender o WCF REST modelo de programação para dar suporte a novos formatos de solicitação de entrada. O exemplo também inclui uma implementação de um formatador que pode desserializar uma solicitação de uma postagem de formulário HTML em um [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] tipo. Além disso, o exemplo usa um modelo T4 para retornar uma página HTML, que fornece um formulário HTML que usuários podem lançar o serviço WCF REST.  
  
## <a name="demonstrates"></a>Demonstra  
  
-   Estendendo o suporte para formatos de solicitação de entrada.  
  
-   Integrar modelos T4.  
  
## <a name="discussion"></a>Discussão  
 Este exemplo consiste em dois projetos. Um projeto é a biblioteca de HtmlFormProcessing que inclui um formatador de solicitação personalizado que pode desserializar postagens do formulário HTML em [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] tipos. O segundo projeto é um aplicativo de console que estende o exemplo de serviço básico do recurso para usar o formatador de solicitação personalizado da biblioteca HtmlFormProcessing.  
  
 O formatador personalizado que pode desserializar postagens de formulário HTML (HtmlFormRequestDispatchFormatter) aceita [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] tipos que podem ser convertidos de uma cadeia de caracteres usando o <xref:System.ServiceModel.Dispatcher.QueryStringConverter> e tipos marcados com <xref:System.Runtime.Serialization.DataContractAttribute> que têm apenas os membros que podem ser convertido de uma cadeia de caracteres usando o QueryStringConverter.  
  
 O projeto de biblioteca HtmlFormProcessing também inclui uma classe base abstrata, `RequestBodyDispatchFormatter`, que pode ser usado para criar outros formatadores de solicitação personalizado. Derivando de `RequestBodyDispatchFormatter` permite que um desenvolvedor se concentre na lógica de desserialização do corpo de solicitação, que permite que a classe base mapear os parâmetros de modelo URI para parâmetros de método da operação. Também na biblioteca HtmlFormProcessing projeto é o `HtmlFormProcessingBehavior` classe, que demonstra como derivar o <xref:System.ServiceModel.Description.WebHttpBehavior> para substituir o formatador de solicitação padrão com um formatador de solicitação personalizado.  
  
 Este projeto de aplicativo de console estende o [serviço básico do recurso](../../../../docs/framework/wcf/samples/basic-resource-service.md) exemplo. O exemplo de serviço básico do recurso demonstra como expor um recurso de uma maneira que usa o modelo de programação WCF REST. No exemplo de serviço básico do recurso, um recurso de coleção do cliente é exposto, de modo que os clientes na coleção podem ser criados, recuperar, atualizados e excluídos. O exemplo de serviço básico de recurso usa apenas os dois suportados nativamente solicitação formatos de entrada, XML e JSON.  
  
 O aplicativo de console neste exemplo de postagem de formulário utiliza o formatador personalizado na biblioteca HtmlFormProcessing, que permite aos usuários criar clientes enviando uma solicitação de uma postagem de formulário HTML usando um navegador. Ele também adiciona uma operação que retorna uma página HTML, que inclui o formulário a ser enviada de volta para o serviço. Esta página HTML é gerada usando um modelo T4 pré-processados, que consiste em um arquivo. TT e um arquivo. cs gerado automaticamente. O arquivo. TT permite que um desenvolvedor gravar uma resposta em um formulário de modelo que contém variáveis e estruturas de controle. Para obter mais informações sobre T4, consulte [gerando artefatos por usando modelos de texto](http://go.microsoft.com/fwlink/?LinkId=178139).  
  
#### <a name="to-run-the-sample"></a>Para executar a amostra  
  
1.  Abra a solução para o exemplo de postagem de formulário. Ao iniciar [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], você deve executar como administrador para executar o exemplo com êxito. Fazer isso clicando com o [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] ícone e selecionando "Executar como administrador" no menu de contexto.  
  
2.  Pressione CTRL + SHIFT + B para compilar a solução e, em seguida, pressione CTRL + F5 para executar o projeto de FormPost do aplicativo de console.  
  
3.  A janela do console é exibida e fornece o URI do serviço em execução e o URI do HTML ajuda a página para o serviço em execução.  
  
4.  Como o exemplo é executado, o cliente grava o status da atividade atual, se ele adicionar um cliente, um cliente de atualização, exclusão de um cliente ou obtendo uma lista de clientes do serviço para a janela do console.  
  
5.  Você precisará, em seguida, navegue até o URI do formulário do cliente. Abra um navegador e navegue para o URI especificado. Digite um nome e o endereço para o cliente e clique no **enviar** botão.  
  
6.  Pressione qualquer tecla para a janela do console continuar a execução do exemplo.  
  
7.  O exemplo for concluído, observe que o cliente que você criou usando o navegador está incluído na lista final de clientes.  
  
8.  Pressione qualquer tecla para encerrar o exemplo.  
  
> [!IMPORTANT]
>  Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos do Windows Workflow Foundation (WF) para o .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos. Este exemplo está localizado no seguinte diretório.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Web\FormPost`
