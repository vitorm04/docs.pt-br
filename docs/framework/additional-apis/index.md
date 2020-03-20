---
title: Bibliotecas de classes e APIs adicionais
ms.date: 11/19/2019
helpviewer_keywords:
- Additional class libraries
- Additional managed libraries
- .NET Framework out-of-band releases
- out-of-band releases
ms.assetid: cf2d9006-b631-4e5d-81cd-20aab78c60f1
ms.topic: conceptual
ms.openlocfilehash: abf7fd20988ebaaaf1a40ccc168c636fd0dacc1d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79155902"
---
# <a name="additional-class-libraries-and-apis"></a>Bibliotecas de classes e APIs adicionais

O Quadro .NET está em constante evolução. Para melhorar o desenvolvimento entre plataformas e introduzir novas funcionalidades mais cedo, novos recursos são lançados fora da banda (OOB). Este tópico lista os projetos OOB para os quais fornecemos documentação.  
  
Além disso, algumas bibliotecas são direcionadas a plataformas específicas ou implementações do .NET Framework. Por exemplo, <xref:System.Text.CodePagesEncodingProvider> a classe disponibiliza codificações de páginas de código para aplicativos UWP desenvolvidos usando o .NET Framework. Este tópico também lista essas bibliotecas.  
  
## <a name="oob-projects"></a>Projetos OOB
  
| Project | Descrição |  
| ------- | ----------- |  
| <xref:System.Collections.Immutable> | Fornece coleções que são thread-safe e têm garantias de que seu conteúdo nunca será alterado. |
| <xref:System.Net.Http.WinHttpHandler> | Fornece um manipulador <xref:System.Net.Http.HttpClient> de mensagens para base na interface WinHTTP do Windows. |
| <xref:System.Numerics> | Fornece uma biblioteca de tipos de vetor que podem aproveitar a aceleração baseada em hardware SIMD.|
| <xref:System.Threading.Tasks.Dataflow> | A Biblioteca de Fluxo de Dados TPL fornece componentes de fluxo de dados para ajudar a aumentar a robustez de aplicativos habilitados para simultaneidade. |  

## <a name="platform-specific-libraries"></a>Bibliotecas específicas da plataforma
  
| Project | Descrição |  
| ------- | ----------- |  
| <xref:System.Text.CodePagesEncodingProvider> | Estende <xref:System.Text.EncodingProvider> a classe para disponibilizar codificações de páginas de código para aplicativos que visam a Plataforma Universal Windows. |  
  
## <a name="private-apis"></a>APIs privadas  

Essas APIs dão suporte à infraestrutura de produto e não se destinam/não têm suporte para uso diretamente do seu código.  
  
* [Microsoft.SqlServer.Server.SmiOrderProperty.Item Property](microsoft.sqlserver.server.smiorderproperty.item.md)
* [System.Exception.PrepForRemoting Method](system.exception.prepforremoting.md)
* [System.Data.SqlTypes.SqlChars.Stream Property](system.data.sqltypes.sqlchars.stream.md)
* [System.Data.SqlTypes.SqlStreamChars Constructor](system.data.sqltypes.sqlstreamchars.-ctor.md)
* [System.Data.SqlTypes.SqlStreamChars.CanSeek Property](system.data.sqltypes.sqlstreamchars.canseek.md)
* [System.Data.SqlTypes.SqlStreamChars.IsNull Property](system.data.sqltypes.sqlstreamchars.isnull.md)
* [System.Data.SqlTypes.SqlStreamChars.Length Property](system.data.sqltypes.sqlstreamchars.length.md)
* [System.Data.SqlTypes.SqlStreamChars.Close Method](system.data.sqltypes.sqlstreamchars.close.md)
* [Método System.Data.SqlTypes.SqlStreamChars.Dispose](system.data.sqltypes.sqlstreamchars.dispose.md)
* [Método System.Data.SqlTypes.SqlStreamChars.Flush](system.data.sqltypes.sqlstreamchars.flush.md)
* [System.Data.SqlTypes.SqlStreamChars.Método de leitura](system.data.sqltypes.sqlstreamchars.read.md)
* [Método System.Data.SqlTypes.SqlStreamChars.Seek](system.data.sqltypes.sqlstreamchars.seek.md)
* [Método System.Data.SqlTypes.SqlStreamChars.SetLength](system.data.sqltypes.sqlstreamchars.setlength.md)
* [Método de gravação system.data.SqlTypes.SqlStreamChars.Write](system.data.sqltypes.sqlstreamchars.write.md)
* [System.IO.MemoryStream.InternalGetOriginAndLength Method](system.io.memorystream.internalgetoriginandlength.md)
* [Classe system.net.connection](connection.md)
* [Campo System.Net.Connection.m\_WriteList](m_writelist.md)
* [Classe System.Net.ConnectionGroup](connectiongroup.md)
* [Campo system.net.connectiongroup.m\_ConnectionList](m_connectionlist.md)
* [Propriedade system.net.connectstream.connection](system.net.connectstream.connection.md)
* [Classe system.net.coreResponseData](coreresponsedata.md)
* [Campo System.Net.CoreResponseData.m\_ResponseHeaders](coreresponsedata_m_responseheaders.md)
* [Campo System.Net.CoreResponseData.m\_StatusCode](coreresponsedata_m_statuscode.md)
* [System.net.httpWebRequest. \_Campo AutoRedirects](_autoredirects.md)
* [System.net.httpWebRequest. \_Campo CoreResponse](httpwebrequest__coreresponse.md)
* [System.net.httpWebRequest. \_Campo httpresponse](_httpresponse.md)
* [Propriedade System.Net.PooledStream.NetworkStream](system.net.pooledstream.networkstream.md)
* [Classe System.Net.RtcState](system.net.rtcstate.md)
* [Campo System.Net.ServicePoint.m\_ConnectionGroupList](m_connectiongrouplist.md)
* [Campo servicepointtable do System.Net.ServicePointManager.s\_](s_servicepointtable.md)
* [Campo System.Net.TlsStream.m_Worker](system.net.tlsstream.m_worker.md)
* [Propriedade System.Net.Security.SslState.SslProtocol](system.net.security.sslstate.sslprotocol.md)
* [System.ServiceModel.Channels.Message.BodyToString Method](system.servicemodel.channels.message.bodytostring.md)
* [Método System.ServiceModel.Channels.Message.WriteStartHeaders](system.servicemodel.channels.message.writestartheaders.md)
* [System.Windows.Diagnostics.s.s\_isDebuggerCheckDisabledDisabledForTestPurposes Field](s-isdebuggercheckdisabledfortestpurposes-field.md)
* [System.Windows.Forms.Design.DataMemberFieldEditor Class](datamemberfieldeditor-class.md)
* [Classe system.windows.forms.design.datamembermembereditor](datamemberlisteditor-class.md)
* [Método System.Xml.XmlReader.CreateSqlReader](system.xml.xmlreader.createsqlreader.md)
* [Adodb. Interface de conexão](adodb.connection.md)
* [Adodb. EventReason Enum](adodb.eventreasonenum.md)
* [Adodb. EventStatus Enum](adodb.eventstatusenum.md)
* [stdole. Estrutura DISPPARAMS](stdole.dispparams.md)
* [stdole. Estrutura EXCEPINFO](stdole.excepinfo.md)
* [stdole. Propriedade IFont.Name](stdole.ifont.name.md)
* [stdole. IFontDisp Interface](stdole.ifontdisp.md)
* [stdole. IPicture.Handle Property](stdole.ipicture.handle.md)
* [stdole. IPictureDisp.Handle Property](stdole.ipicturedisp.handle.md)
* [stdole. StdFont Interface](stdole.stdfont.md)
* [stdole. StdPicture Interface](stdole.stdpicture.md)
  
## <a name="see-also"></a>Confira também

* [O .NET Framework e lançamentos fora da banda](../get-started/the-net-framework-and-out-of-band-releases.md)
