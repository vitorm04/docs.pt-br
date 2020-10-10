---
title: Bibliotecas de classes e APIs adicionais
description: Explore bibliotecas de classes e APIs adicionais no .NET, incluindo projetos de OOB (fora de banda), bibliotecas específicas de plataforma e APIs privadas.
ms.date: 08/11/2020
helpviewer_keywords:
- Additional class libraries
- Additional managed libraries
- .NET Framework out-of-band releases
- out-of-band releases
ms.assetid: cf2d9006-b631-4e5d-81cd-20aab78c60f1
ms.topic: conceptual
ms.openlocfilehash: 55cb37cc2c9184eeb55ee0aab39e97f4a3f7b7d8
ms.sourcegitcommit: eb7e87496f42361b1da98562dd75b516c9d58bbc
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/09/2020
ms.locfileid: "91877633"
---
# <a name="additional-class-libraries-and-apis"></a><span data-ttu-id="b095a-103">Bibliotecas de classes e APIs adicionais</span><span class="sxs-lookup"><span data-stu-id="b095a-103">Additional class libraries and APIs</span></span>

<span data-ttu-id="b095a-104">Este artigo lista .NET Framework APIs que foram lançadas fora de banda, visam uma plataforma específica ou são tipos privados ou internos.</span><span class="sxs-lookup"><span data-stu-id="b095a-104">This article lists .NET Framework APIs that either were released out of band, target a specific platform, or are private or internal types.</span></span>

## <a name="oob-projects"></a><span data-ttu-id="b095a-105">Projetos OOB</span><span class="sxs-lookup"><span data-stu-id="b095a-105">OOB projects</span></span>

<span data-ttu-id="b095a-106">Para melhorar o desenvolvimento de plataforma cruzada e introduzir novas funcionalidades no início, alguns recursos .NET Framework foram lançados fora de banda (OOB).</span><span class="sxs-lookup"><span data-stu-id="b095a-106">To improve cross-platform development and introduce new functionality early, some .NET Framework features were released out of band (OOB).</span></span>

| <span data-ttu-id="b095a-107">Projeto</span><span class="sxs-lookup"><span data-stu-id="b095a-107">Project</span></span> | <span data-ttu-id="b095a-108">Descrição</span><span class="sxs-lookup"><span data-stu-id="b095a-108">Description</span></span> |
| ------- | ----------- |
| <xref:System.Collections.Immutable> | <span data-ttu-id="b095a-109">Fornece coleções que são thread-safe e têm garantias de que seu conteúdo nunca será alterado.</span><span class="sxs-lookup"><span data-stu-id="b095a-109">Provides collections that are thread safe and guaranteed to never change their contents.</span></span> |
| <xref:System.Net.Http.WinHttpHandler> | <span data-ttu-id="b095a-110">Fornece um manipulador de mensagens para <xref:System.Net.Http.HttpClient> o com base na interface WinHTTP do Windows.</span><span class="sxs-lookup"><span data-stu-id="b095a-110">Provides a message handler for <xref:System.Net.Http.HttpClient> based on the WinHTTP interface of Windows.</span></span> |
| <xref:System.Numerics> | <span data-ttu-id="b095a-111">Fornece uma biblioteca de tipos de vetor que podem aproveitar a aceleração baseada em hardware SIMD.</span><span class="sxs-lookup"><span data-stu-id="b095a-111">Provides a library of vector types that can take advantage of SIMD hardware-based acceleration.</span></span>|
| <xref:System.Threading.Tasks.Dataflow> | <span data-ttu-id="b095a-112">A Biblioteca de Fluxo de Dados TPL fornece componentes de fluxo de dados para ajudar a aumentar a robustez de aplicativos habilitados para simultaneidade.</span><span class="sxs-lookup"><span data-stu-id="b095a-112">The TPL Dataflow Library provides dataflow components to help increase the robustness of concurrency-enabled applications.</span></span> |

## <a name="platform-specific-libraries"></a><span data-ttu-id="b095a-113">Bibliotecas específicas da plataforma</span><span class="sxs-lookup"><span data-stu-id="b095a-113">Platform-specific libraries</span></span>

<span data-ttu-id="b095a-114">Algumas bibliotecas têm como destino plataformas específicas.</span><span class="sxs-lookup"><span data-stu-id="b095a-114">Some libraries target specific platforms.</span></span> <span data-ttu-id="b095a-115">Por exemplo, a <xref:System.Text.CodePagesEncodingProvider> classe torna codificações de página de código disponíveis para aplicativos UWP desenvolvidos usando .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="b095a-115">For example, the <xref:System.Text.CodePagesEncodingProvider> class makes code page encodings available to UWP apps developed using .NET Framework.</span></span>

| <span data-ttu-id="b095a-116">Projeto</span><span class="sxs-lookup"><span data-stu-id="b095a-116">Project</span></span> | <span data-ttu-id="b095a-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="b095a-117">Description</span></span> |
| ------- | ----------- |
| <xref:System.Text.CodePagesEncodingProvider> | <span data-ttu-id="b095a-118">Estende a <xref:System.Text.EncodingProvider> classe para tornar as codificações de página de código disponíveis para aplicativos direcionados ao plataforma universal do Windows.</span><span class="sxs-lookup"><span data-stu-id="b095a-118">Extends the <xref:System.Text.EncodingProvider> class to make code page encodings available to apps that target the Universal Windows Platform.</span></span> |

## <a name="private-apis"></a><span data-ttu-id="b095a-119">APIs privadas</span><span class="sxs-lookup"><span data-stu-id="b095a-119">Private APIs</span></span>

<span data-ttu-id="b095a-120">Essas APIs dão suporte à infraestrutura do produto e não são pretendidas nem têm suporte para serem usadas diretamente do seu código.</span><span class="sxs-lookup"><span data-stu-id="b095a-120">These APIs support the product infrastructure and are not intended or supported to be used directly from your code.</span></span>

* [<span data-ttu-id="b095a-121">Propriedade Microsoft. SqlServer. Server. SmiOrderProperty. Item</span><span class="sxs-lookup"><span data-stu-id="b095a-121">Microsoft.SqlServer.Server.SmiOrderProperty.Item property</span></span>](microsoft.sqlserver.server.smiorderproperty.item.md)
* [<span data-ttu-id="b095a-122">Método System. Exception. PrepForRemoting</span><span class="sxs-lookup"><span data-stu-id="b095a-122">System.Exception.PrepForRemoting method</span></span>](system.exception.prepforremoting.md)
* [<span data-ttu-id="b095a-123">Propriedade System. Data. SqlTypes. SqlChars. Stream</span><span class="sxs-lookup"><span data-stu-id="b095a-123">System.Data.SqlTypes.SqlChars.Stream property</span></span>](system.data.sqltypes.sqlchars.stream.md)
* [<span data-ttu-id="b095a-124">Construtor System. Data. SqlTypes. SqlStreamChars</span><span class="sxs-lookup"><span data-stu-id="b095a-124">System.Data.SqlTypes.SqlStreamChars Constructor</span></span>](system.data.sqltypes.sqlstreamchars.-ctor.md)
* [<span data-ttu-id="b095a-125">Propriedade System. Data. SqlTypes. SqlStreamChars. CanSeek</span><span class="sxs-lookup"><span data-stu-id="b095a-125">System.Data.SqlTypes.SqlStreamChars.CanSeek property</span></span>](system.data.sqltypes.sqlstreamchars.canseek.md)
* [<span data-ttu-id="b095a-126">Propriedade System. Data. SqlTypes. SqlStreamChars. IsNull</span><span class="sxs-lookup"><span data-stu-id="b095a-126">System.Data.SqlTypes.SqlStreamChars.IsNull property</span></span>](system.data.sqltypes.sqlstreamchars.isnull.md)
* [<span data-ttu-id="b095a-127">Propriedade System. Data. sqltipations. SqlStreamChars. Length</span><span class="sxs-lookup"><span data-stu-id="b095a-127">System.Data.SqlTypes.SqlStreamChars.Length property</span></span>](system.data.sqltypes.sqlstreamchars.length.md)
* [<span data-ttu-id="b095a-128">Método System. Data. SqlTypes. SqlStreamChars. Close</span><span class="sxs-lookup"><span data-stu-id="b095a-128">System.Data.SqlTypes.SqlStreamChars.Close method</span></span>](system.data.sqltypes.sqlstreamchars.close.md)
* [<span data-ttu-id="b095a-129">Método System. Data. SqlTypes. SqlStreamChars. Dispose</span><span class="sxs-lookup"><span data-stu-id="b095a-129">System.Data.SqlTypes.SqlStreamChars.Dispose method</span></span>](system.data.sqltypes.sqlstreamchars.dispose.md)
* [<span data-ttu-id="b095a-130">Método System. Data. sqltipations. SqlStreamChars. Flush</span><span class="sxs-lookup"><span data-stu-id="b095a-130">System.Data.SqlTypes.SqlStreamChars.Flush method</span></span>](system.data.sqltypes.sqlstreamchars.flush.md)
* [<span data-ttu-id="b095a-131">Método System. Data. SqlTypes. SqlStreamChars. Read</span><span class="sxs-lookup"><span data-stu-id="b095a-131">System.Data.SqlTypes.SqlStreamChars.Read method</span></span>](system.data.sqltypes.sqlstreamchars.read.md)
* [<span data-ttu-id="b095a-132">Método System. Data. SqlTypes. SqlStreamChars. Seek</span><span class="sxs-lookup"><span data-stu-id="b095a-132">System.Data.SqlTypes.SqlStreamChars.Seek method</span></span>](system.data.sqltypes.sqlstreamchars.seek.md)
* [<span data-ttu-id="b095a-133">Método System. Data. SqlTypes. SqlStreamChars. SetLength</span><span class="sxs-lookup"><span data-stu-id="b095a-133">System.Data.SqlTypes.SqlStreamChars.SetLength method</span></span>](system.data.sqltypes.sqlstreamchars.setlength.md)
* [<span data-ttu-id="b095a-134">Método System. Data. SqlTypes. SqlStreamChars. Write</span><span class="sxs-lookup"><span data-stu-id="b095a-134">System.Data.SqlTypes.SqlStreamChars.Write method</span></span>](system.data.sqltypes.sqlstreamchars.write.md)
* [<span data-ttu-id="b095a-135">Método System. IO. MemoryStream. InternalGetOriginAndLength</span><span class="sxs-lookup"><span data-stu-id="b095a-135">System.IO.MemoryStream.InternalGetOriginAndLength method</span></span>](system.io.memorystream.internalgetoriginandlength.md)
* [<span data-ttu-id="b095a-136">Classe System .net. ComNetOS</span><span class="sxs-lookup"><span data-stu-id="b095a-136">System.Net.ComNetOS class</span></span>](system.net.comnetos.md)
* [<span data-ttu-id="b095a-137">Classe System .net. Connection</span><span class="sxs-lookup"><span data-stu-id="b095a-137">System.Net.Connection class</span></span>](connection.md)
* [<span data-ttu-id="b095a-138">Campo de gravação System .net. Connection. m \_</span><span class="sxs-lookup"><span data-stu-id="b095a-138">System.Net.Connection.m\_WriteList field</span></span>](m_writelist.md)
* [<span data-ttu-id="b095a-139">Classe System .net. ConnectionObject</span><span class="sxs-lookup"><span data-stu-id="b095a-139">System.Net.ConnectionGroup class</span></span>](connectiongroup.md)
* [<span data-ttu-id="b095a-140">Campo de conexão do sistema .net. Connectionlist. m \_</span><span class="sxs-lookup"><span data-stu-id="b095a-140">System.Net.ConnectionGroup.m\_ConnectionList field</span></span>](m_connectionlist.md)
* [<span data-ttu-id="b095a-141">Propriedade System .net. ConnectStream. Connection</span><span class="sxs-lookup"><span data-stu-id="b095a-141">System.Net.ConnectStream.Connection property</span></span>](system.net.connectstream.connection.md)
* [<span data-ttu-id="b095a-142">Classe System .net. CoreResponseData</span><span class="sxs-lookup"><span data-stu-id="b095a-142">System.Net.CoreResponseData class</span></span>](coreresponsedata.md)
* [<span data-ttu-id="b095a-143">Campo System .net. CoreResponseData. m \_ ResponseHeaders</span><span class="sxs-lookup"><span data-stu-id="b095a-143">System.Net.CoreResponseData.m\_ResponseHeaders field</span></span>](coreresponsedata_m_responseheaders.md)
* [<span data-ttu-id="b095a-144">Campo de StatusCode System .net. CoreResponseData. m \_</span><span class="sxs-lookup"><span data-stu-id="b095a-144">System.Net.CoreResponseData.m\_StatusCode field</span></span>](coreresponsedata_m_statuscode.md)
* [<span data-ttu-id="b095a-145">Classe System .net. ExceptionHelper</span><span class="sxs-lookup"><span data-stu-id="b095a-145">System.Net.ExceptionHelper class</span></span>](system.net.exceptionhelper.md)
* [<span data-ttu-id="b095a-146">Classe System .net. HttpStatusDescription</span><span class="sxs-lookup"><span data-stu-id="b095a-146">System.Net.HttpStatusDescription class</span></span>](system.net.httpstatusdescription.md)
* [<span data-ttu-id="b095a-147">System .net. HttpWebRequest. \_ Campo de redirecionamento</span><span class="sxs-lookup"><span data-stu-id="b095a-147">System.Net.HttpWebRequest.\_AutoRedirects field</span></span>](_autoredirects.md)
* [<span data-ttu-id="b095a-148">System .net. HttpWebRequest. \_ Campo CoreResponse</span><span class="sxs-lookup"><span data-stu-id="b095a-148">System.Net.HttpWebRequest.\_CoreResponse field</span></span>](httpwebrequest__coreresponse.md)
* [<span data-ttu-id="b095a-149">System .net. HttpWebRequest. \_ Campo HttpResponse</span><span class="sxs-lookup"><span data-stu-id="b095a-149">System.Net.HttpWebRequest.\_HttpResponse field</span></span>](_httpresponse.md)
* [<span data-ttu-id="b095a-150">Classe System .net. Logging</span><span class="sxs-lookup"><span data-stu-id="b095a-150">System.Net.Logging class</span></span>](system.net.logging.md)
* [<span data-ttu-id="b095a-151">Classe System .net. mail. MailAddressParser</span><span class="sxs-lookup"><span data-stu-id="b095a-151">System.Net.Mail.MailAddressParser class</span></span>](system.net.mail.mailaddressparser.md)
* [<span data-ttu-id="b095a-152">Classe System .net. mail. QuotedPairReader</span><span class="sxs-lookup"><span data-stu-id="b095a-152">System.Net.Mail.QuotedPairReader class</span></span>](system.net.mail.quotedpairreader.md)
* [<span data-ttu-id="b095a-153">Classe System .net. MIME. MailBnfHelper</span><span class="sxs-lookup"><span data-stu-id="b095a-153">System.Net.Mime.MailBnfHelper class</span></span>](system.net.mime.mailbnfhelper.md)
* [<span data-ttu-id="b095a-154">Propriedade System .net. PooledStream. NetworkStream</span><span class="sxs-lookup"><span data-stu-id="b095a-154">System.Net.PooledStream.NetworkStream property</span></span>](system.net.pooledstream.networkstream.md)
* [<span data-ttu-id="b095a-155">Classe System .net. RtcState</span><span class="sxs-lookup"><span data-stu-id="b095a-155">System.Net.RtcState class</span></span>](system.net.rtcstate.md)
* [<span data-ttu-id="b095a-156">Propriedade System .net. Security. SslState. SslProtocol</span><span class="sxs-lookup"><span data-stu-id="b095a-156">System.Net.Security.SslState.SslProtocol property</span></span>](system.net.security.sslstate.sslprotocol.md)
* [<span data-ttu-id="b095a-157">Campo System .net. ConnectionGroupList. m \_</span><span class="sxs-lookup"><span data-stu-id="b095a-157">System.Net.ServicePoint.m\_ConnectionGroupList field</span></span>](m_connectiongrouplist.md)
* [<span data-ttu-id="b095a-158">Método System .net. ServicePointManager. CloseConnectionGroups</span><span class="sxs-lookup"><span data-stu-id="b095a-158">System.Net.ServicePointManager.CloseConnectionGroups method</span></span>](system.net.servicepointmanager.closeconnectiongroups.md)
* [<span data-ttu-id="b095a-159">Campo System .net. ServicePointManager. s do \_ Objectpointtable</span><span class="sxs-lookup"><span data-stu-id="b095a-159">System.Net.ServicePointManager.s\_ServicePointTable field</span></span>](s_servicepointtable.md)
* [<span data-ttu-id="b095a-160">Campo de System.Net.TlsStream.m_Worker</span><span class="sxs-lookup"><span data-stu-id="b095a-160">System.Net.TlsStream.m_Worker field</span></span>](system.net.tlsstream.m_worker.md)
* [<span data-ttu-id="b095a-161">Classe System .net. UnsafeNclNativeMethods</span><span class="sxs-lookup"><span data-stu-id="b095a-161">System.Net.UnsafeNclNativeMethods class</span></span>](system.net.unsafenclnativemethods.md)
* [<span data-ttu-id="b095a-162">Método System .net. WebHeaderCollection. addinterna</span><span class="sxs-lookup"><span data-stu-id="b095a-162">System.Net.WebHeaderCollection.AddInternal method</span></span>](system.net.webheadercollection.addinternal.md)
* [<span data-ttu-id="b095a-163">Método System. ServiceModel. Channels. Message. BodyToString</span><span class="sxs-lookup"><span data-stu-id="b095a-163">System.ServiceModel.Channels.Message.BodyToString method</span></span>](system.servicemodel.channels.message.bodytostring.md)
* [<span data-ttu-id="b095a-164">Método System. ServiceModel. Channels. Message. WriteStartHeaders</span><span class="sxs-lookup"><span data-stu-id="b095a-164">System.ServiceModel.Channels.Message.WriteStartHeaders method</span></span>](system.servicemodel.channels.message.writestartheaders.md)
* [<span data-ttu-id="b095a-165">Classe System. Web. Compilation. ControlBuilderInterceptor</span><span class="sxs-lookup"><span data-stu-id="b095a-165">System.Web.Compilation.ControlBuilderInterceptor class</span></span>](controlbuilderinterceptor-class.md)
* [<span data-ttu-id="b095a-166">Método System. Windows. Controls. GridViewHeaderRowPresenter. FindHeaderByColumn</span><span class="sxs-lookup"><span data-stu-id="b095a-166">System.Windows.Controls.GridViewHeaderRowPresenter.FindHeaderByColumn method</span></span>](system.windows.controls.gridviewheaderrowpresenter.findheaderbycolumn.md)
* [<span data-ttu-id="b095a-167">Método System. Windows. Controls. GridViewHeaderRowPresenter. MakeParentItemsControlGotFocus</span><span class="sxs-lookup"><span data-stu-id="b095a-167">System.Windows.Controls.GridViewHeaderRowPresenter.MakeParentItemsControlGotFocus method</span></span>](system.windows.controls.gridviewheaderrowpresenter.makeparentitemscontrolgotfocus.md)
* [<span data-ttu-id="b095a-168">Método System. Windows. Controls. GridViewHeaderRowPresenter. PrepareHeaderDrag</span><span class="sxs-lookup"><span data-stu-id="b095a-168">System.Windows.Controls.GridViewHeaderRowPresenter.PrepareHeaderDrag method</span></span>](system.windows.controls.gridviewheaderrowpresenter.prepareheaderdrag.md)
* [<span data-ttu-id="b095a-169">Campo System. Windows. Diagnostics. VisualDiagnostics. s \_ isDebuggerCheckDisabledForTestPurposes</span><span class="sxs-lookup"><span data-stu-id="b095a-169">System.Windows.Diagnostics.VisualDiagnostics.s\_isDebuggerCheckDisabledForTestPurposes field</span></span>](s-isdebuggercheckdisabledfortestpurposes-field.md)
* [<span data-ttu-id="b095a-170">Classe System. Windows. Forms. Design. DataMemberFieldEditor</span><span class="sxs-lookup"><span data-stu-id="b095a-170">System.Windows.Forms.Design.DataMemberFieldEditor class</span></span>](datamemberfieldeditor-class.md)
* [<span data-ttu-id="b095a-171">Classe System. Windows. Forms. Design. DataMemberListEditor</span><span class="sxs-lookup"><span data-stu-id="b095a-171">System.Windows.Forms.Design.DataMemberListEditor class</span></span>](datamemberlisteditor-class.md)
* [<span data-ttu-id="b095a-172"> MétodoSystem.Xml.XmlReader. CreateSqlReader</span><span class="sxs-lookup"><span data-stu-id="b095a-172">System.Xml.XmlReader.CreateSqlReader method</span></span>](system.xml.xmlreader.createsqlreader.md)
* [<span data-ttu-id="b095a-173">ActiveX. Interface de conexão</span><span class="sxs-lookup"><span data-stu-id="b095a-173">adodb.Connection interface</span></span>](adodb.connection.md)
* [<span data-ttu-id="b095a-174">ActiveX. EventReason enum</span><span class="sxs-lookup"><span data-stu-id="b095a-174">adodb.EventReason enum</span></span>](adodb.eventreasonenum.md)
* [<span data-ttu-id="b095a-175">ActiveX. EventStatus enum</span><span class="sxs-lookup"><span data-stu-id="b095a-175">adodb.EventStatus enum</span></span>](adodb.eventstatusenum.md)
* [<span data-ttu-id="b095a-176">stdole. Estrutura DISPPARAMS</span><span class="sxs-lookup"><span data-stu-id="b095a-176">stdole.DISPPARAMS Structure</span></span>](stdole.dispparams.md)
* [<span data-ttu-id="b095a-177">stdole. Estrutura EXCEPINFO</span><span class="sxs-lookup"><span data-stu-id="b095a-177">stdole.EXCEPINFO Structure</span></span>](stdole.excepinfo.md)
* [<span data-ttu-id="b095a-178">stdole. Propriedade IFont.Name</span><span class="sxs-lookup"><span data-stu-id="b095a-178">stdole.IFont.Name property</span></span>](stdole.ifont.name.md)
* [<span data-ttu-id="b095a-179">stdole. Interface IFontDisp</span><span class="sxs-lookup"><span data-stu-id="b095a-179">stdole.IFontDisp interface</span></span>](stdole.ifontdisp.md)
* [<span data-ttu-id="b095a-180">stdole. Propriedade IPicture. Handle</span><span class="sxs-lookup"><span data-stu-id="b095a-180">stdole.IPicture.Handle property</span></span>](stdole.ipicture.handle.md)
* [<span data-ttu-id="b095a-181">stdole. Propriedade IPictureDisp. Handle</span><span class="sxs-lookup"><span data-stu-id="b095a-181">stdole.IPictureDisp.Handle property</span></span>](stdole.ipicturedisp.handle.md)
* [<span data-ttu-id="b095a-182">stdole. Interface StdFont</span><span class="sxs-lookup"><span data-stu-id="b095a-182">stdole.StdFont interface</span></span>](stdole.stdfont.md)
* [<span data-ttu-id="b095a-183">stdole. Interface StdPicture</span><span class="sxs-lookup"><span data-stu-id="b095a-183">stdole.StdPicture interface</span></span>](stdole.stdpicture.md)

## <a name="see-also"></a><span data-ttu-id="b095a-184">Confira também</span><span class="sxs-lookup"><span data-stu-id="b095a-184">See also</span></span>

* [<span data-ttu-id="b095a-185">.NET Framework e versões fora de banda</span><span class="sxs-lookup"><span data-stu-id="b095a-185">.NET Framework and Out-of-Band Releases</span></span>](../get-started/the-net-framework-and-out-of-band-releases.md)
