---
title: Bibliotecas de classes e APIs adicionais
ms.date: 11/19/2019
helpviewer_keywords:
- Additional class libraries
- Additional managed libraries
- .NET Framework out-of-band releases
- out-of-band releases
ms.assetid: cf2d9006-b631-4e5d-81cd-20aab78c60f1
author: mairaw
ms.author: mairaw
ms.topic: conceptual
ms.openlocfilehash: e1e2af584c73b1c0b2548cdd3fcbd8517dfa330d
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74429342"
---
# <a name="additional-class-libraries-and-apis"></a>Bibliotecas de classes e APIs adicionais

A .NET Framework está constantemente evoluindo. Para melhorar o desenvolvimento de plataforma cruzada e introduzir novas funcionalidades desde o início, novos recursos são lançados fora de banda (OOB). Este tópico lista os projetos OOB para os quais fornecemos documentação.  
  
Além disso, algumas bibliotecas são direcionadas a plataformas específicas ou implementações do .NET Framework. Por exemplo, a classe <xref:System.Text.CodePagesEncodingProvider> torna codificações de página de código disponíveis para aplicativos UWP desenvolvidos usando o .NET Framework. Este tópico também lista essas bibliotecas.  
  
## <a name="oob-projects"></a>Projetos OOB
  
| {1&gt;Projeto&lt;1} | Descrição |  
| ------- | ----------- |  
| <xref:System.Collections.Immutable> | Fornece coleções que são thread-safe e têm garantias de que seu conteúdo nunca será alterado. |
| <xref:System.Net.Http.WinHttpHandler> | Fornece um manipulador de mensagens para <xref:System.Net.Http.HttpClient> com base na interface WinHTTP do Windows. |
| <xref:System.Numerics> | Fornece uma biblioteca de tipos de vetor que podem aproveitar a aceleração baseada em hardware SIMD.| 
| <xref:System.Threading.Tasks.Dataflow> | A Biblioteca de Fluxo de Dados TPL fornece componentes de fluxo de dados para ajudar a aumentar a robustez de aplicativos habilitados para simultaneidade. |  

## <a name="platform-specific-libraries"></a>Bibliotecas específicas da plataforma
  
| {1&gt;Projeto&lt;1} | Descrição |  
| ------- | ----------- |  
| <xref:System.Text.CodePagesEncodingProvider> | Estende a classe <xref:System.Text.EncodingProvider> para disponibilizar codificações de página de código para aplicativos direcionados ao Plataforma Universal do Windows. |  
  
## <a name="private-apis"></a>APIs privadas  

Essas APIs dão suporte à infraestrutura de produto e não se destinam/não têm suporte para uso diretamente do seu código.  
  
* [Propriedade Microsoft. SqlServer. Server. SmiOrderProperty. Item](microsoft.sqlserver.server.smiorderproperty.item.md)
* [Método System. Exception. PrepForRemoting](system.exception.prepforremoting.md)
* [Propriedade System. Data. SqlTypes. SqlChars. Stream](system.data.sqltypes.sqlchars.stream.md)
* [Construtor System. Data. SqlTypes. SqlStreamChars](system.data.sqltypes.sqlstreamchars.-ctor.md)
* [Propriedade System. Data. SqlTypes. SqlStreamChars. CanSeek](system.data.sqltypes.sqlstreamchars.canseek.md)
* [Propriedade System. Data. SqlTypes. SqlStreamChars. IsNull](system.data.sqltypes.sqlstreamchars.isnull.md)
* [Propriedade System. Data. sqltipations. SqlStreamChars. Length](system.data.sqltypes.sqlstreamchars.length.md)
* [Método System. Data. SqlTypes. SqlStreamChars. Close](system.data.sqltypes.sqlstreamchars.close.md)
* [Método System. Data. SqlTypes. SqlStreamChars. Dispose](system.data.sqltypes.sqlstreamchars.dispose.md)
* [Método System. Data. sqltipations. SqlStreamChars. Flush](system.data.sqltypes.sqlstreamchars.flush.md)
* [Método System. Data. SqlTypes. SqlStreamChars. Read](system.data.sqltypes.sqlstreamchars.read.md)
* [Método System. Data. SqlTypes. SqlStreamChars. Seek](system.data.sqltypes.sqlstreamchars.seek.md)
* [Método System. Data. SqlTypes. SqlStreamChars. SetLength](system.data.sqltypes.sqlstreamchars.setlength.md)
* [Método System. Data. SqlTypes. SqlStreamChars. Write](system.data.sqltypes.sqlstreamchars.write.md)
* [Método System. IO. MemoryStream. InternalGetOriginAndLength](system.io.memorystream.internalgetoriginandlength.md)
* [Classe System .net. Connection](connection.md)
* [System .net. Connection. m\_campo Writelist](m_writelist.md)
* [Classe System .net. ConnectionObject](connectiongroup.md)
* [Sistema .net. Connection. m\_campo Connectionlist](m_connectionlist.md)
* [Propriedade System .net. ConnectStream. Connection](system.net.connectstream.connection.md)
* [Classe System .net. CoreResponseData](coreresponsedata.md)
* [System .net. CoreResponseData. m\_campo ResponseHeaders](coreresponsedata_m_responseheaders.md)
* [System .net. CoreResponseData. m\_campo StatusCode](coreresponsedata_m_statuscode.md)
* [Campo System .net. HttpWebRequest.\_redirecionamentos](_autoredirects.md)
* [Campo System .net. HttpWebRequest.\_CoreResponse](httpwebrequest__coreresponse.md)
* [Campo System .net. HttpWebRequest.\_HttpResponse](_httpresponse.md)
* [Propriedade System .net. PooledStream. NetworkStream](system.net.pooledstream.networkstream.md)
* [Classe System .net. RtcState](system.net.rtcstate.md)
* [System .net. ConnectionGroupList. m\_campo de](m_connectiongrouplist.md)
* [System .net. ServicePointManager. s\_campo do objectpointtable](s_servicepointtable.md)
* [Campo System .net. TlsStream. m_Worker](system.net.tlsstream.m_worker.md)
* [Propriedade System .net. Security. SslState. SslProtocol](system.net.security.sslstate.sslprotocol.md)
* [Método System. ServiceModel. Channels. Message. BodyToString](system.servicemodel.channels.message.bodytostring.md)
* [Método System. ServiceModel. Channels. Message. WriteStartHeaders](system.servicemodel.channels.message.writestartheaders.md)
* [System. Windows. Diagnostics. VisualDiagnostics. s\_campo isDebuggerCheckDisabledForTestPurposes](s-isdebuggercheckdisabledfortestpurposes-field.md)
* [Classe System. Windows. Forms. Design. DataMemberFieldEditor](datamemberfieldeditor-class.md)
* [Classe System. Windows. Forms. Design. DataMemberListEditor](datamemberlisteditor-class.md)
* [Método System. xml. XmlReader. CreateSqlReader](system.xml.xmlreader.createsqlreader.md)
* [ActiveX. Interface de conexão](adodb.connection.md)
* [ActiveX. EventReason enum](adodb.eventreasonenum.md)
* [ActiveX. EventStatus enum](adodb.eventstatusenum.md)
* [stdole. Estrutura DISPPARAMS](stdole.dispparams.md)
* [stdole. Estrutura EXCEPINFO](stdole.excepinfo.md)
* [stdole. Propriedade IFont.Name](stdole.ifont.name.md)
* [stdole. Interface IFontDisp](stdole.ifontdisp.md)
* [stdole. Propriedade IPicture. Handle](stdole.ipicture.handle.md)
* [stdole. Propriedade IPictureDisp. Handle](stdole.ipicturedisp.handle.md)
* [stdole. Interface StdFont](stdole.stdfont.md)
* [stdole. Interface StdPicture](stdole.stdpicture.md)
  
## <a name="see-also"></a>Consulte também

* [O .NET Framework e lançamentos fora da banda](../get-started/the-net-framework-and-out-of-band-releases.md)
