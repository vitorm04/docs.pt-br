---
title: Derivando de WebResponse
ms.date: 03/30/2017
helpviewer_keywords:
- Deriving from WebResponse
ms.assetid: f11d4866-a199-4087-9306-a5a4c18b13db
ms.openlocfilehash: 6bdb21b8aaf8deb39e3abd68a69a9a5a10247e6f
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59226039"
---
# <a name="deriving-from-webresponse"></a>Derivando de WebResponse
A classe <xref:System.Net.WebResponse> é uma classe base abstrata que fornece os métodos e as propriedades básicas para criar uma resposta específica ao protocolo que se ajusta ao modelo de protocolo conectável do .NET Framework. Os aplicativos que usam a classe <xref:System.Net.WebRequest> para solicitar dados de recursos recebem as respostas em uma **WebResponse**. Os descendentes de **WebResponse** específicos ao protocolo devem implementar os membros abstratos da classe **WebResponse**.  
  
 A classe **WebRequest** associada deve criar descendentes de **WebResponse**. Por exemplo, as instâncias <xref:System.Net.HttpWebResponse> são criadas apenas como o resultado da chamada a <xref:System.Net.HttpWebRequest.GetResponse%2A?displayProperty=nameWithType> ou <xref:System.Net.HttpWebRequest.EndGetResponse%2A?displayProperty=nameWithType>. Cada **WebResponse** contém o resultado de uma solicitação para um recurso e não se destina a ser reutilizada.  
  
## <a name="contentlength-property"></a>Propriedade ContentLength  
 A propriedade <xref:System.Net.WebResponse.ContentLength%2A> indica o número de bytes de dados disponíveis no fluxo retornado pelo método <xref:System.Net.WebResponse.GetResponseStream%2A>. A propriedade **ContentLength** não indica o número de bytes de informações de cabeçalho ou de metadados retornados pelo servidor; indica somente o número de bytes de dados no próprio recurso solicitado.  
  
## <a name="contenttype-property"></a>Propriedade ContentType  
 A propriedade <xref:System.Net.WebResponse.ContentType%2A> fornece informações especiais que o protocolo exige que sejam enviadas ao cliente para identificar o tipo de conteúdo que está sendo enviado pelo servidor. Normalmente, esse é o tipo de conteúdo MIME dos dados retornados.  
  
## <a name="headers-property"></a>Propriedade Headers  
 A propriedade <xref:System.Net.WebResponse.Headers%2A> contém uma coleção arbitrária de pares de nome/valor de metadados associados à resposta. Todos os metadados necessários para o protocolo que podem ser expressos como um par nome/valor podem ser incluídos na propriedade **Headers**.  
  
 Não é necessário usar a propriedade **Headers** para usar os metadados do cabeçalho. Os metadados específicos ao protocolo podem ser expostos como propriedades; por exemplo, a propriedade <xref:System.Net.HttpWebResponse.LastModified%2A?displayProperty=nameWithType> expõe o cabeçalho HTTP **Last-Modified**. Ao expor os metadados do cabeçalho como uma propriedade, você não deve permitir que a mesma propriedade seja definida usando a propriedade **Headers**.  
  
## <a name="responseuri-property"></a>Propriedade ResponseUri  
 A propriedade <xref:System.Net.WebResponse.ResponseUri%2A> contém o URI do recurso que, de fato, forneceu a resposta. Para protocolos que não dão suporte ao redirecionamento, o **ResponseUri** será o mesmo que a propriedade <xref:System.Net.WebRequest.RequestUri%2A> da **WebRequest** que criou a resposta. Se o protocolo der suporte ao redirecionamento da solicitação, o **ResponseUri** conterá o URI da resposta.  
  
## <a name="close-method"></a>Método Close  
 O método <xref:System.Net.WebResponse.Close%2A> fecha todas as conexões feitas pela solicitação e pela resposta e limpa os recursos usados pela resposta. O método **Close** fecha todas as instâncias de fluxo usadas pela resposta, mas não gera uma exceção se o fluxo de resposta foi fechado anteriormente por uma chamada ao método <xref:System.IO.Stream.Close%2A?displayProperty=nameWithType>.  
  
## <a name="getresponsestream-method"></a>Método GetResponseStream  
 O método <xref:System.Net.WebResponse.GetResponseStream%2A> retorna um fluxo que contém a resposta do recurso solicitado. O fluxo de resposta contém apenas os dados retornados pelo recurso; o cabeçalho ou os metadados incluídos na resposta devem ser removidos da resposta e expostos ao aplicativo por meio de propriedades específicas ao protocolo ou da propriedade **Headers**.  
  
 A instância de fluxo retornada pelo método **GetResponseStream** pertence ao aplicativo e pode ser fechada sem fechar a **WebResponse**. Por convenção, uma chamada ao método **WebResponse.Close** também fecha o fluxo retornado por **GetResponse**.  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Net.WebResponse>
- <xref:System.Net.HttpWebResponse>
- <xref:System.Net.FileWebResponse>
- [Programando protocolos conectáveis](../../../docs/framework/network-programming/programming-pluggable-protocols.md)
- [Derivando de WebRequest](../../../docs/framework/network-programming/deriving-from-webrequest.md)
