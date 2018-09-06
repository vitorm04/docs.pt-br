---
title: Postagem de formulário
ms.date: 03/30/2017
ms.assetid: fa6f84f9-2e07-4e3c-92d0-a245308b7dff
ms.openlocfilehash: 9115b9abfa7039bf409bb9bbce54e5012d05a074
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/06/2018
ms.locfileid: "43890822"
---
# <a name="form-post"></a>Postagem de formulário
Este exemplo demonstra como estender o WCF modelo de programação REST para dar suporte a novos formatos de solicitação de entrada. O exemplo também inclui uma implementação de um formatador que pode desserializar uma solicitação de uma postagem de formulário HTML para um [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] tipo. Além disso, o exemplo usa um modelo T4 para retornar uma página HTML, que fornece o formulário HTML que os usuários podem postar de volta para o serviço REST do WCF.  
  
## <a name="demonstrates"></a>Demonstra  
  
-   Estendendo o suporte para formatos de solicitação de entrada.  
  
-   Integrando modelos T4.  
  
## <a name="discussion"></a>Discussão  
 Esse exemplo consiste em dois projetos. Um projeto é a biblioteca de HtmlFormProcessing que inclui um formatador de solicitação personalizado que pode desserializar postagens de formulário HTML em [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] tipos. O segundo projeto é um aplicativo de console que estende o exemplo de serviço básico de recursos para usar o formatador de solicitação personalizado da biblioteca HtmlFormProcessing.  
  
 O formatador personalizado que pode desserializar postagens de formulário HTML (HtmlFormRequestDispatchFormatter) aceita [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] tipos que podem ser convertidos de uma cadeia de caracteres usando o <xref:System.ServiceModel.Dispatcher.QueryStringConverter> e tipos marcados com <xref:System.Runtime.Serialization.DataContractAttribute> que só têm membros que podem ser convertido de uma cadeia de caracteres usando o QueryStringConverter.  
  
 O projeto de biblioteca HtmlFormProcessing também inclui uma classe base abstrata, `RequestBodyDispatchFormatter`, que pode ser usado para criar outros formatadores de solicitação personalizado. Deriva o `RequestBodyDispatchFormatter` permite que um desenvolvedor se concentre na lógica de desserialização do corpo de solicitação, que permite que a classe base mapear os parâmetros de modelo URI aos parâmetros do método da operação. Também na biblioteca do HtmlFormProcessing projeto é o `HtmlFormProcessingBehavior` classe, que demonstra como derivar a <xref:System.ServiceModel.Description.WebHttpBehavior> para substituir o formatador de solicitação padrão por um formatador de solicitação personalizado.  
  
 Este projeto de aplicativo de console estende o [serviço básico de recursos](../../../../docs/framework/wcf/samples/basic-resource-service.md) exemplo. O exemplo de serviço básico do recurso demonstra como expor um recurso de uma maneira que usa o modelo de programação REST do WCF. No exemplo de serviço básico de recursos, um recurso de coleção do cliente é exposto, de modo que os clientes na coleção podem ser criados, recuperados, atualizados e excluídos. O exemplo de serviço básico de recursos usa apenas os dois suportados nativamente entrada solicitação formatos, XML e JSON.  
  
 O aplicativo de console neste exemplo de postagem de formulário utiliza o formatador personalizado na biblioteca do HtmlFormProcessing, que permite aos usuários criar clientes enviando uma solicitação de um post de formulário HTML usando um navegador. Ele também adiciona uma operação que retorna uma página HTML, que inclui o formulário a ser postada de volta para o serviço. Essa página HTML é gerada usando um modelo T4 pré-processado, que consiste em um arquivo. TT e um arquivo. cs do gerado automaticamente. O arquivo. TT permite que um desenvolvedor escreva uma resposta em um formulário de modelo que contém variáveis e estruturas de controle. Para obter mais informações sobre T4, consulte [gerando artefatos por usando modelos de texto](https://go.microsoft.com/fwlink/?LinkId=178139).  
  
#### <a name="to-run-the-sample"></a>Para executar a amostra  
  
1.  Abra a solução para o exemplo de postagem de formulário. Ao iniciar [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], você deve executar como administrador para executar o exemplo com êxito. Fazer isso clicando com o [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] ícone e escolhendo "Executar como administrador" no menu de contexto.  
  
2.  Pressione CTRL + SHIFT + B para compilar a solução e, em seguida, pressione CTRL + F5 para executar o projeto de FormPost do aplicativo de console.  
  
3.  A janela do console é exibida e fornece o URI do serviço em execução e o URI do HTML na página para a execução do serviço de Ajuda.  
  
4.  Como o exemplo é executado, o cliente grava o status da atividade atual, se ele adicionando um cliente, atualizando um cliente, a exclusão de um cliente ou obtendo uma lista de clientes atuais do serviço para a janela do console.  
  
5.  Você precisará, em seguida, navegue até o URI do formulário do cliente. Abra um navegador e navegue até um determinado URI. Digite um nome e o endereço para o cliente e clique o **enviar** botão.  
  
6.  Pressione qualquer tecla para a janela do console continuar a execução do exemplo.  
  
7.  À medida que a amostra for concluída, observe que o cliente que você criou usando o navegador está incluído na lista final de clientes.  
  
8.  Pressione qualquer tecla para encerrar a amostra.  
  
> [!IMPORTANT]
>  Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e o Windows Workflow Foundation (WF) exemplos do .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos. Este exemplo está localizado no seguinte diretório.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Web\FormPost`
