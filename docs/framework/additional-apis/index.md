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
# <a name="additional-class-libraries-and-apis"></a><span data-ttu-id="17f14-102">Bibliotecas de classes e APIs adicionais</span><span class="sxs-lookup"><span data-stu-id="17f14-102">Additional class libraries and APIs</span></span>

<span data-ttu-id="17f14-103">O Quadro .NET está em constante evolução.</span><span class="sxs-lookup"><span data-stu-id="17f14-103">The .NET Framework is constantly evolving.</span></span> <span data-ttu-id="17f14-104">Para melhorar o desenvolvimento entre plataformas e introduzir novas funcionalidades mais cedo, novos recursos são lançados fora da banda (OOB).</span><span class="sxs-lookup"><span data-stu-id="17f14-104">To improve cross-platform development and introduce new functionality early, new features are released out of band (OOB).</span></span> <span data-ttu-id="17f14-105">Este tópico lista os projetos OOB para os quais fornecemos documentação.</span><span class="sxs-lookup"><span data-stu-id="17f14-105">This topic lists the OOB projects that we provide documentation for.</span></span>  
  
<span data-ttu-id="17f14-106">Além disso, algumas bibliotecas são direcionadas a plataformas específicas ou implementações do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="17f14-106">In addition, some libraries target specific platforms or implementations of the .NET Framework.</span></span> <span data-ttu-id="17f14-107">Por exemplo, <xref:System.Text.CodePagesEncodingProvider> a classe disponibiliza codificações de páginas de código para aplicativos UWP desenvolvidos usando o .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="17f14-107">For example, the <xref:System.Text.CodePagesEncodingProvider> class makes code page encodings available to UWP apps developed using the .NET Framework.</span></span> <span data-ttu-id="17f14-108">Este tópico também lista essas bibliotecas.</span><span class="sxs-lookup"><span data-stu-id="17f14-108">This topic lists these libraries as well.</span></span>  
  
## <a name="oob-projects"></a><span data-ttu-id="17f14-109">Projetos OOB</span><span class="sxs-lookup"><span data-stu-id="17f14-109">OOB projects</span></span>
  
| <span data-ttu-id="17f14-110">Project</span><span class="sxs-lookup"><span data-stu-id="17f14-110">Project</span></span> | <span data-ttu-id="17f14-111">Descrição</span><span class="sxs-lookup"><span data-stu-id="17f14-111">Description</span></span> |  
| ------- | ----------- |  
| <xref:System.Collections.Immutable> | <span data-ttu-id="17f14-112">Fornece coleções que são thread-safe e têm garantias de que seu conteúdo nunca será alterado.</span><span class="sxs-lookup"><span data-stu-id="17f14-112">Provides collections that are thread safe and guaranteed to never change their contents.</span></span> |
| <xref:System.Net.Http.WinHttpHandler> | <span data-ttu-id="17f14-113">Fornece um manipulador <xref:System.Net.Http.HttpClient> de mensagens para base na interface WinHTTP do Windows.</span><span class="sxs-lookup"><span data-stu-id="17f14-113">Provides a message handler for <xref:System.Net.Http.HttpClient> based on the WinHTTP interface of Windows.</span></span> |
| <xref:System.Numerics> | <span data-ttu-id="17f14-114">Fornece uma biblioteca de tipos de vetor que podem aproveitar a aceleração baseada em hardware SIMD.</span><span class="sxs-lookup"><span data-stu-id="17f14-114">Provides a library of vector types that can take advantage of SIMD hardware-based acceleration.</span></span>|
| <xref:System.Threading.Tasks.Dataflow> | <span data-ttu-id="17f14-115">A Biblioteca de Fluxo de Dados TPL fornece componentes de fluxo de dados para ajudar a aumentar a robustez de aplicativos habilitados para simultaneidade.</span><span class="sxs-lookup"><span data-stu-id="17f14-115">The TPL Dataflow Library provides dataflow components to help increase the robustness of concurrency-enabled applications.</span></span> |  

## <a name="platform-specific-libraries"></a><span data-ttu-id="17f14-116">Bibliotecas específicas da plataforma</span><span class="sxs-lookup"><span data-stu-id="17f14-116">Platform-specific libraries</span></span>
  
| <span data-ttu-id="17f14-117">Project</span><span class="sxs-lookup"><span data-stu-id="17f14-117">Project</span></span> | <span data-ttu-id="17f14-118">Descrição</span><span class="sxs-lookup"><span data-stu-id="17f14-118">Description</span></span> |  
| ------- | ----------- |  
| <xref:System.Text.CodePagesEncodingProvider> | <span data-ttu-id="17f14-119">Estende <xref:System.Text.EncodingProvider> a classe para disponibilizar codificações de páginas de código para aplicativos que visam a Plataforma Universal Windows.</span><span class="sxs-lookup"><span data-stu-id="17f14-119">Extends the <xref:System.Text.EncodingProvider> class to make code page encodings available to apps that target the Universal Windows Platform.</span></span> |  
  
## <a name="private-apis"></a><span data-ttu-id="17f14-120">APIs privadas</span><span class="sxs-lookup"><span data-stu-id="17f14-120">Private APIs</span></span>  

<span data-ttu-id="17f14-121">Essas APIs dão suporte à infraestrutura de produto e não se destinam/não têm suporte para uso diretamente do seu código.</span><span class="sxs-lookup"><span data-stu-id="17f14-121">These APIs support the product infrastructure and are not intended/supported to be used directly from your code.</span></span>  
  
* [<span data-ttu-id="17f14-122">Microsoft.SqlServer.Server.SmiOrderProperty.Item Property</span><span class="sxs-lookup"><span data-stu-id="17f14-122">Microsoft.SqlServer.Server.SmiOrderProperty.Item Property</span></span>](microsoft.sqlserver.server.smiorderproperty.item.md)
* [<span data-ttu-id="17f14-123">System.Exception.PrepForRemoting Method</span><span class="sxs-lookup"><span data-stu-id="17f14-123">System.Exception.PrepForRemoting Method</span></span>](system.exception.prepforremoting.md)
* [<span data-ttu-id="17f14-124">System.Data.SqlTypes.SqlChars.Stream Property</span><span class="sxs-lookup"><span data-stu-id="17f14-124">System.Data.SqlTypes.SqlChars.Stream Property</span></span>](system.data.sqltypes.sqlchars.stream.md)
* [<span data-ttu-id="17f14-125">System.Data.SqlTypes.SqlStreamChars Constructor</span><span class="sxs-lookup"><span data-stu-id="17f14-125">System.Data.SqlTypes.SqlStreamChars Constructor</span></span>](system.data.sqltypes.sqlstreamchars.-ctor.md)
* [<span data-ttu-id="17f14-126">System.Data.SqlTypes.SqlStreamChars.CanSeek Property</span><span class="sxs-lookup"><span data-stu-id="17f14-126">System.Data.SqlTypes.SqlStreamChars.CanSeek Property</span></span>](system.data.sqltypes.sqlstreamchars.canseek.md)
* [<span data-ttu-id="17f14-127">System.Data.SqlTypes.SqlStreamChars.IsNull Property</span><span class="sxs-lookup"><span data-stu-id="17f14-127">System.Data.SqlTypes.SqlStreamChars.IsNull Property</span></span>](system.data.sqltypes.sqlstreamchars.isnull.md)
* [<span data-ttu-id="17f14-128">System.Data.SqlTypes.SqlStreamChars.Length Property</span><span class="sxs-lookup"><span data-stu-id="17f14-128">System.Data.SqlTypes.SqlStreamChars.Length Property</span></span>](system.data.sqltypes.sqlstreamchars.length.md)
* [<span data-ttu-id="17f14-129">System.Data.SqlTypes.SqlStreamChars.Close Method</span><span class="sxs-lookup"><span data-stu-id="17f14-129">System.Data.SqlTypes.SqlStreamChars.Close Method</span></span>](system.data.sqltypes.sqlstreamchars.close.md)
* [<span data-ttu-id="17f14-130">Método System.Data.SqlTypes.SqlStreamChars.Dispose</span><span class="sxs-lookup"><span data-stu-id="17f14-130">System.Data.SqlTypes.SqlStreamChars.Dispose Method</span></span>](system.data.sqltypes.sqlstreamchars.dispose.md)
* [<span data-ttu-id="17f14-131">Método System.Data.SqlTypes.SqlStreamChars.Flush</span><span class="sxs-lookup"><span data-stu-id="17f14-131">System.Data.SqlTypes.SqlStreamChars.Flush Method</span></span>](system.data.sqltypes.sqlstreamchars.flush.md)
* [<span data-ttu-id="17f14-132">System.Data.SqlTypes.SqlStreamChars.Método de leitura</span><span class="sxs-lookup"><span data-stu-id="17f14-132">System.Data.SqlTypes.SqlStreamChars.Read Method</span></span>](system.data.sqltypes.sqlstreamchars.read.md)
* [<span data-ttu-id="17f14-133">Método System.Data.SqlTypes.SqlStreamChars.Seek</span><span class="sxs-lookup"><span data-stu-id="17f14-133">System.Data.SqlTypes.SqlStreamChars.Seek Method</span></span>](system.data.sqltypes.sqlstreamchars.seek.md)
* [<span data-ttu-id="17f14-134">Método System.Data.SqlTypes.SqlStreamChars.SetLength</span><span class="sxs-lookup"><span data-stu-id="17f14-134">System.Data.SqlTypes.SqlStreamChars.SetLength Method</span></span>](system.data.sqltypes.sqlstreamchars.setlength.md)
* [<span data-ttu-id="17f14-135">Método de gravação system.data.SqlTypes.SqlStreamChars.Write</span><span class="sxs-lookup"><span data-stu-id="17f14-135">System.Data.SqlTypes.SqlStreamChars.Write Method</span></span>](system.data.sqltypes.sqlstreamchars.write.md)
* [<span data-ttu-id="17f14-136">System.IO.MemoryStream.InternalGetOriginAndLength Method</span><span class="sxs-lookup"><span data-stu-id="17f14-136">System.IO.MemoryStream.InternalGetOriginAndLength Method</span></span>](system.io.memorystream.internalgetoriginandlength.md)
* [<span data-ttu-id="17f14-137">Classe system.net.connection</span><span class="sxs-lookup"><span data-stu-id="17f14-137">System.Net.Connection Class</span></span>](connection.md)
* [<span data-ttu-id="17f14-138">Campo System.Net.Connection.m\_WriteList</span><span class="sxs-lookup"><span data-stu-id="17f14-138">System.Net.Connection.m\_WriteList Field</span></span>](m_writelist.md)
* [<span data-ttu-id="17f14-139">Classe System.Net.ConnectionGroup</span><span class="sxs-lookup"><span data-stu-id="17f14-139">System.Net.ConnectionGroup Class</span></span>](connectiongroup.md)
* [<span data-ttu-id="17f14-140">Campo system.net.connectiongroup.m\_ConnectionList</span><span class="sxs-lookup"><span data-stu-id="17f14-140">System.Net.ConnectionGroup.m\_ConnectionList Field</span></span>](m_connectionlist.md)
* [<span data-ttu-id="17f14-141">Propriedade system.net.connectstream.connection</span><span class="sxs-lookup"><span data-stu-id="17f14-141">System.Net.ConnectStream.Connection Property</span></span>](system.net.connectstream.connection.md)
* [<span data-ttu-id="17f14-142">Classe system.net.coreResponseData</span><span class="sxs-lookup"><span data-stu-id="17f14-142">System.Net.CoreResponseData Class</span></span>](coreresponsedata.md)
* [<span data-ttu-id="17f14-143">Campo System.Net.CoreResponseData.m\_ResponseHeaders</span><span class="sxs-lookup"><span data-stu-id="17f14-143">System.Net.CoreResponseData.m\_ResponseHeaders Field</span></span>](coreresponsedata_m_responseheaders.md)
* [<span data-ttu-id="17f14-144">Campo System.Net.CoreResponseData.m\_StatusCode</span><span class="sxs-lookup"><span data-stu-id="17f14-144">System.Net.CoreResponseData.m\_StatusCode Field</span></span>](coreresponsedata_m_statuscode.md)
* [<span data-ttu-id="17f14-145">System.net.httpWebRequest. \_Campo AutoRedirects</span><span class="sxs-lookup"><span data-stu-id="17f14-145">System.Net.HttpWebRequest.\_AutoRedirects Field</span></span>](_autoredirects.md)
* [<span data-ttu-id="17f14-146">System.net.httpWebRequest. \_Campo CoreResponse</span><span class="sxs-lookup"><span data-stu-id="17f14-146">System.Net.HttpWebRequest.\_CoreResponse Field</span></span>](httpwebrequest__coreresponse.md)
* [<span data-ttu-id="17f14-147">System.net.httpWebRequest. \_Campo httpresponse</span><span class="sxs-lookup"><span data-stu-id="17f14-147">System.Net.HttpWebRequest.\_HttpResponse Field</span></span>](_httpresponse.md)
* [<span data-ttu-id="17f14-148">Propriedade System.Net.PooledStream.NetworkStream</span><span class="sxs-lookup"><span data-stu-id="17f14-148">System.Net.PooledStream.NetworkStream Property</span></span>](system.net.pooledstream.networkstream.md)
* [<span data-ttu-id="17f14-149">Classe System.Net.RtcState</span><span class="sxs-lookup"><span data-stu-id="17f14-149">System.Net.RtcState class</span></span>](system.net.rtcstate.md)
* [<span data-ttu-id="17f14-150">Campo System.Net.ServicePoint.m\_ConnectionGroupList</span><span class="sxs-lookup"><span data-stu-id="17f14-150">System.Net.ServicePoint.m\_ConnectionGroupList Field</span></span>](m_connectiongrouplist.md)
* [<span data-ttu-id="17f14-151">Campo servicepointtable do System.Net.ServicePointManager.s\_</span><span class="sxs-lookup"><span data-stu-id="17f14-151">System.Net.ServicePointManager.s\_ServicePointTable Field</span></span>](s_servicepointtable.md)
* [<span data-ttu-id="17f14-152">Campo System.Net.TlsStream.m_Worker</span><span class="sxs-lookup"><span data-stu-id="17f14-152">System.Net.TlsStream.m_Worker Field</span></span>](system.net.tlsstream.m_worker.md)
* [<span data-ttu-id="17f14-153">Propriedade System.Net.Security.SslState.SslProtocol</span><span class="sxs-lookup"><span data-stu-id="17f14-153">System.Net.Security.SslState.SslProtocol Property</span></span>](system.net.security.sslstate.sslprotocol.md)
* [<span data-ttu-id="17f14-154">System.ServiceModel.Channels.Message.BodyToString Method</span><span class="sxs-lookup"><span data-stu-id="17f14-154">System.ServiceModel.Channels.Message.BodyToString Method</span></span>](system.servicemodel.channels.message.bodytostring.md)
* [<span data-ttu-id="17f14-155">Método System.ServiceModel.Channels.Message.WriteStartHeaders</span><span class="sxs-lookup"><span data-stu-id="17f14-155">System.ServiceModel.Channels.Message.WriteStartHeaders Method</span></span>](system.servicemodel.channels.message.writestartheaders.md)
* [<span data-ttu-id="17f14-156">System.Windows.Diagnostics.s.s\_isDebuggerCheckDisabledDisabledForTestPurposes Field</span><span class="sxs-lookup"><span data-stu-id="17f14-156">System.Windows.Diagnostics.VisualDiagnostics.s\_isDebuggerCheckDisabledForTestPurposes Field</span></span>](s-isdebuggercheckdisabledfortestpurposes-field.md)
* [<span data-ttu-id="17f14-157">System.Windows.Forms.Design.DataMemberFieldEditor Class</span><span class="sxs-lookup"><span data-stu-id="17f14-157">System.Windows.Forms.Design.DataMemberFieldEditor Class</span></span>](datamemberfieldeditor-class.md)
* [<span data-ttu-id="17f14-158">Classe system.windows.forms.design.datamembermembereditor</span><span class="sxs-lookup"><span data-stu-id="17f14-158">System.Windows.Forms.Design.DataMemberListEditor Class</span></span>](datamemberlisteditor-class.md)
* [<span data-ttu-id="17f14-159">Método System.Xml.XmlReader.CreateSqlReader</span><span class="sxs-lookup"><span data-stu-id="17f14-159">System.Xml.XmlReader.CreateSqlReader Method</span></span>](system.xml.xmlreader.createsqlreader.md)
* [<span data-ttu-id="17f14-160">Adodb. Interface de conexão</span><span class="sxs-lookup"><span data-stu-id="17f14-160">adodb.Connection Interface</span></span>](adodb.connection.md)
* [<span data-ttu-id="17f14-161">Adodb. EventReason Enum</span><span class="sxs-lookup"><span data-stu-id="17f14-161">adodb.EventReason Enum</span></span>](adodb.eventreasonenum.md)
* [<span data-ttu-id="17f14-162">Adodb. EventStatus Enum</span><span class="sxs-lookup"><span data-stu-id="17f14-162">adodb.EventStatus Enum</span></span>](adodb.eventstatusenum.md)
* [<span data-ttu-id="17f14-163">stdole. Estrutura DISPPARAMS</span><span class="sxs-lookup"><span data-stu-id="17f14-163">stdole.DISPPARAMS Structure</span></span>](stdole.dispparams.md)
* [<span data-ttu-id="17f14-164">stdole. Estrutura EXCEPINFO</span><span class="sxs-lookup"><span data-stu-id="17f14-164">stdole.EXCEPINFO Structure</span></span>](stdole.excepinfo.md)
* [<span data-ttu-id="17f14-165">stdole. Propriedade IFont.Name</span><span class="sxs-lookup"><span data-stu-id="17f14-165">stdole.IFont.Name Property</span></span>](stdole.ifont.name.md)
* [<span data-ttu-id="17f14-166">stdole. IFontDisp Interface</span><span class="sxs-lookup"><span data-stu-id="17f14-166">stdole.IFontDisp Interface</span></span>](stdole.ifontdisp.md)
* [<span data-ttu-id="17f14-167">stdole. IPicture.Handle Property</span><span class="sxs-lookup"><span data-stu-id="17f14-167">stdole.IPicture.Handle Property</span></span>](stdole.ipicture.handle.md)
* [<span data-ttu-id="17f14-168">stdole. IPictureDisp.Handle Property</span><span class="sxs-lookup"><span data-stu-id="17f14-168">stdole.IPictureDisp.Handle Property</span></span>](stdole.ipicturedisp.handle.md)
* [<span data-ttu-id="17f14-169">stdole. StdFont Interface</span><span class="sxs-lookup"><span data-stu-id="17f14-169">stdole.StdFont Interface</span></span>](stdole.stdfont.md)
* [<span data-ttu-id="17f14-170">stdole. StdPicture Interface</span><span class="sxs-lookup"><span data-stu-id="17f14-170">stdole.StdPicture Interface</span></span>](stdole.stdpicture.md)
  
## <a name="see-also"></a><span data-ttu-id="17f14-171">Confira também</span><span class="sxs-lookup"><span data-stu-id="17f14-171">See also</span></span>

* [<span data-ttu-id="17f14-172">O .NET Framework e lançamentos fora da banda</span><span class="sxs-lookup"><span data-stu-id="17f14-172">The .NET Framework and Out-of-Band Releases</span></span>](../get-started/the-net-framework-and-out-of-band-releases.md)
