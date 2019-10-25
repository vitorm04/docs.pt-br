---
title: Bibliotecas de classes e APIs adicionais
ms.date: 10/17/2019
helpviewer_keywords:
- Additional class libraries
- Additional managed libraries
- .NET Framework out-of-band releases
- out-of-band releases
ms.assetid: cf2d9006-b631-4e5d-81cd-20aab78c60f1
author: mairaw
ms.author: mairaw
ms.topic: conceptual
ms.openlocfilehash: 4b47847e9d6e9424d4442d655c40a637383c7229
ms.sourcegitcommit: 337bdc5a463875daf2cc6883e5a2da97d56f5000
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/24/2019
ms.locfileid: "72847077"
---
# <a name="additional-class-libraries-and-apis"></a><span data-ttu-id="0a39c-102">Bibliotecas de classes e APIs adicionais</span><span class="sxs-lookup"><span data-stu-id="0a39c-102">Additional class libraries and APIs</span></span>

<span data-ttu-id="0a39c-103">A .NET Framework está constantemente evoluindo.</span><span class="sxs-lookup"><span data-stu-id="0a39c-103">The .NET Framework is constantly evolving.</span></span> <span data-ttu-id="0a39c-104">Para melhorar o desenvolvimento de plataforma cruzada e introduzir novas funcionalidades desde o início, novos recursos são lançados fora de banda (OOB).</span><span class="sxs-lookup"><span data-stu-id="0a39c-104">To improve cross-platform development and introduce new functionality early, new features are released out of band (OOB).</span></span> <span data-ttu-id="0a39c-105">Este tópico lista os projetos OOB para os quais fornecemos documentação.</span><span class="sxs-lookup"><span data-stu-id="0a39c-105">This topic lists the OOB projects that we provide documentation for.</span></span>  
  
<span data-ttu-id="0a39c-106">Além disso, algumas bibliotecas são direcionadas a plataformas específicas ou implementações do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="0a39c-106">In addition, some libraries target specific platforms or implementations of the .NET Framework.</span></span> <span data-ttu-id="0a39c-107">Por exemplo, a classe <xref:System.Text.CodePagesEncodingProvider> torna codificações de página de código disponíveis para aplicativos UWP desenvolvidos usando o .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="0a39c-107">For example, the <xref:System.Text.CodePagesEncodingProvider> class makes code page encodings available to UWP apps developed using the .NET Framework.</span></span> <span data-ttu-id="0a39c-108">Este tópico também lista essas bibliotecas.</span><span class="sxs-lookup"><span data-stu-id="0a39c-108">This topic lists these libraries as well.</span></span>  
  
## <a name="oob-projects"></a><span data-ttu-id="0a39c-109">Projetos OOB</span><span class="sxs-lookup"><span data-stu-id="0a39c-109">OOB projects</span></span>
  
| <span data-ttu-id="0a39c-110">Projeto</span><span class="sxs-lookup"><span data-stu-id="0a39c-110">Project</span></span> | <span data-ttu-id="0a39c-111">Descrição</span><span class="sxs-lookup"><span data-stu-id="0a39c-111">Description</span></span> |  
| ------- | ----------- |  
| <xref:System.Collections.Immutable> | <span data-ttu-id="0a39c-112">Fornece coleções que são thread-safe e têm garantias de que seu conteúdo nunca será alterado.</span><span class="sxs-lookup"><span data-stu-id="0a39c-112">Provides collections that are thread safe and guaranteed to never change their contents.</span></span> |
| <xref:System.Net.Http.WinHttpHandler> | <span data-ttu-id="0a39c-113">Fornece um manipulador de mensagens para <xref:System.Net.Http.HttpClient> com base na interface WinHTTP do Windows.</span><span class="sxs-lookup"><span data-stu-id="0a39c-113">Provides a message handler for <xref:System.Net.Http.HttpClient> based on the WinHTTP interface of Windows.</span></span> |
| <xref:System.Numerics> | <span data-ttu-id="0a39c-114">Fornece uma biblioteca de tipos de vetor que podem aproveitar a aceleração baseada em hardware SIMD.</span><span class="sxs-lookup"><span data-stu-id="0a39c-114">Provides a library of vector types that can take advantage of SIMD hardware-based acceleration.</span></span>| 
| <xref:System.Threading.Tasks.Dataflow> | <span data-ttu-id="0a39c-115">A Biblioteca de Fluxo de Dados TPL fornece componentes de fluxo de dados para ajudar a aumentar a robustez de aplicativos habilitados para simultaneidade.</span><span class="sxs-lookup"><span data-stu-id="0a39c-115">The TPL Dataflow Library provides dataflow components to help increase the robustness of concurrency-enabled applications.</span></span> |  

## <a name="platform-specific-libraries"></a><span data-ttu-id="0a39c-116">Bibliotecas específicas da plataforma</span><span class="sxs-lookup"><span data-stu-id="0a39c-116">Platform-specific libraries</span></span>
  
| <span data-ttu-id="0a39c-117">Projeto</span><span class="sxs-lookup"><span data-stu-id="0a39c-117">Project</span></span> | <span data-ttu-id="0a39c-118">Descrição</span><span class="sxs-lookup"><span data-stu-id="0a39c-118">Description</span></span> |  
| ------- | ----------- |  
| <xref:System.Text.CodePagesEncodingProvider> | <span data-ttu-id="0a39c-119">Estende a classe <xref:System.Text.EncodingProvider> para disponibilizar codificações de página de código para aplicativos direcionados ao Plataforma Universal do Windows.</span><span class="sxs-lookup"><span data-stu-id="0a39c-119">Extends the <xref:System.Text.EncodingProvider> class to make code page encodings available to apps that target the Universal Windows Platform.</span></span> |  
  
## <a name="private-apis"></a><span data-ttu-id="0a39c-120">APIs privadas</span><span class="sxs-lookup"><span data-stu-id="0a39c-120">Private APIs</span></span>  

<span data-ttu-id="0a39c-121">Essas APIs dão suporte à infraestrutura de produto e não se destinam/não têm suporte para uso diretamente do seu código.</span><span class="sxs-lookup"><span data-stu-id="0a39c-121">These APIs support the product infrastructure and are not intended/supported to be used directly from your code.</span></span>  
  
* [<span data-ttu-id="0a39c-122">Propriedade Microsoft. SqlServer. Server. SmiOrderProperty. Item</span><span class="sxs-lookup"><span data-stu-id="0a39c-122">Microsoft.SqlServer.Server.SmiOrderProperty.Item Property</span></span>](microsoft.sqlserver.server.smiorderproperty.item.md)
* [<span data-ttu-id="0a39c-123">Método System. Exception. PrepForRemoting</span><span class="sxs-lookup"><span data-stu-id="0a39c-123">System.Exception.PrepForRemoting Method</span></span>](system.exception.prepforremoting.md)
* [<span data-ttu-id="0a39c-124">Propriedade System. Data. SqlTypes. SqlChars. Stream</span><span class="sxs-lookup"><span data-stu-id="0a39c-124">System.Data.SqlTypes.SqlChars.Stream Property</span></span>](system.data.sqltypes.sqlchars.stream.md)
* [<span data-ttu-id="0a39c-125">Construtor System. Data. SqlTypes. SqlStreamChars</span><span class="sxs-lookup"><span data-stu-id="0a39c-125">System.Data.SqlTypes.SqlStreamChars Constructor</span></span>](system.data.sqltypes.sqlstreamchars.-ctor.md)
* [<span data-ttu-id="0a39c-126">Propriedade System. Data. SqlTypes. SqlStreamChars. CanSeek</span><span class="sxs-lookup"><span data-stu-id="0a39c-126">System.Data.SqlTypes.SqlStreamChars.CanSeek Property</span></span>](system.data.sqltypes.sqlstreamchars.canseek.md)
* [<span data-ttu-id="0a39c-127">Propriedade System. Data. SqlTypes. SqlStreamChars. IsNull</span><span class="sxs-lookup"><span data-stu-id="0a39c-127">System.Data.SqlTypes.SqlStreamChars.IsNull Property</span></span>](system.data.sqltypes.sqlstreamchars.isnull.md)
* [<span data-ttu-id="0a39c-128">Propriedade System. Data. sqltipations. SqlStreamChars. Length</span><span class="sxs-lookup"><span data-stu-id="0a39c-128">System.Data.SqlTypes.SqlStreamChars.Length Property</span></span>](system.data.sqltypes.sqlstreamchars.length.md)
* [<span data-ttu-id="0a39c-129">Método System. Data. SqlTypes. SqlStreamChars. Close</span><span class="sxs-lookup"><span data-stu-id="0a39c-129">System.Data.SqlTypes.SqlStreamChars.Close Method</span></span>](system.data.sqltypes.sqlstreamchars.close.md)
* [<span data-ttu-id="0a39c-130">Método System. Data. SqlTypes. SqlStreamChars. Dispose</span><span class="sxs-lookup"><span data-stu-id="0a39c-130">System.Data.SqlTypes.SqlStreamChars.Dispose Method</span></span>](system.data.sqltypes.sqlstreamchars.dispose.md)
* [<span data-ttu-id="0a39c-131">Método System. Data. sqltipations. SqlStreamChars. Flush</span><span class="sxs-lookup"><span data-stu-id="0a39c-131">System.Data.SqlTypes.SqlStreamChars.Flush Method</span></span>](system.data.sqltypes.sqlstreamchars.flush.md)
* [<span data-ttu-id="0a39c-132">Método System. Data. SqlTypes. SqlStreamChars. Read</span><span class="sxs-lookup"><span data-stu-id="0a39c-132">System.Data.SqlTypes.SqlStreamChars.Read Method</span></span>](system.data.sqltypes.sqlstreamchars.read.md)
* [<span data-ttu-id="0a39c-133">Método System. Data. SqlTypes. SqlStreamChars. Seek</span><span class="sxs-lookup"><span data-stu-id="0a39c-133">System.Data.SqlTypes.SqlStreamChars.Seek Method</span></span>](system.data.sqltypes.sqlstreamchars.seek.md)
* [<span data-ttu-id="0a39c-134">Método System. Data. SqlTypes. SqlStreamChars. SetLength</span><span class="sxs-lookup"><span data-stu-id="0a39c-134">System.Data.SqlTypes.SqlStreamChars.SetLength Method</span></span>](system.data.sqltypes.sqlstreamchars.setlength.md)
* [<span data-ttu-id="0a39c-135">Método System. Data. SqlTypes. SqlStreamChars. Write</span><span class="sxs-lookup"><span data-stu-id="0a39c-135">System.Data.SqlTypes.SqlStreamChars.Write Method</span></span>](system.data.sqltypes.sqlstreamchars.write.md)
* [<span data-ttu-id="0a39c-136">Classe System .net. Connection</span><span class="sxs-lookup"><span data-stu-id="0a39c-136">System.Net.Connection Class</span></span>](connection.md)
* [<span data-ttu-id="0a39c-137">System .net. Connection. m\_campo Writelist</span><span class="sxs-lookup"><span data-stu-id="0a39c-137">System.Net.Connection.m\_WriteList Field</span></span>](m_writelist.md)
* [<span data-ttu-id="0a39c-138">Classe System .net. ConnectionObject</span><span class="sxs-lookup"><span data-stu-id="0a39c-138">System.Net.ConnectionGroup Class</span></span>](connectiongroup.md)
* [<span data-ttu-id="0a39c-139">Sistema .net. Connection. m\_campo Connectionlist</span><span class="sxs-lookup"><span data-stu-id="0a39c-139">System.Net.ConnectionGroup.m\_ConnectionList Field</span></span>](m_connectionlist.md)
* [<span data-ttu-id="0a39c-140">Propriedade System .net. ConnectStream. Connection</span><span class="sxs-lookup"><span data-stu-id="0a39c-140">System.Net.ConnectStream.Connection Property</span></span>](system.net.connectstream.connection.md)
* [<span data-ttu-id="0a39c-141">Classe System .net. CoreResponseData</span><span class="sxs-lookup"><span data-stu-id="0a39c-141">System.Net.CoreResponseData Class</span></span>](coreresponsedata.md)
* [<span data-ttu-id="0a39c-142">System .net. CoreResponseData. m\_campo ResponseHeaders</span><span class="sxs-lookup"><span data-stu-id="0a39c-142">System.Net.CoreResponseData.m\_ResponseHeaders Field</span></span>](coreresponsedata_m_responseheaders.md)
* [<span data-ttu-id="0a39c-143">System .net. CoreResponseData. m\_campo StatusCode</span><span class="sxs-lookup"><span data-stu-id="0a39c-143">System.Net.CoreResponseData.m\_StatusCode Field</span></span>](coreresponsedata_m_statuscode.md)
* [<span data-ttu-id="0a39c-144">Campo System .net. HttpWebRequest.\_redirecionamentos</span><span class="sxs-lookup"><span data-stu-id="0a39c-144">System.Net.HttpWebRequest.\_AutoRedirects Field</span></span>](_autoredirects.md)
* [<span data-ttu-id="0a39c-145">Campo System .net. HttpWebRequest.\_CoreResponse</span><span class="sxs-lookup"><span data-stu-id="0a39c-145">System.Net.HttpWebRequest.\_CoreResponse Field</span></span>](httpwebrequest__coreresponse.md)
* [<span data-ttu-id="0a39c-146">Campo System .net. HttpWebRequest.\_HttpResponse</span><span class="sxs-lookup"><span data-stu-id="0a39c-146">System.Net.HttpWebRequest.\_HttpResponse Field</span></span>](_httpresponse.md)
* [<span data-ttu-id="0a39c-147">Propriedade System .net. PooledStream. NetworkStream</span><span class="sxs-lookup"><span data-stu-id="0a39c-147">System.Net.PooledStream.NetworkStream Property</span></span>](system.net.pooledstream.networkstream.md)
* [<span data-ttu-id="0a39c-148">System .net. ConnectionGroupList. m\_campo de</span><span class="sxs-lookup"><span data-stu-id="0a39c-148">System.Net.ServicePoint.m\_ConnectionGroupList Field</span></span>](m_connectiongrouplist.md)
* [<span data-ttu-id="0a39c-149">System .net. ServicePointManager. s\_campo do objectpointtable</span><span class="sxs-lookup"><span data-stu-id="0a39c-149">System.Net.ServicePointManager.s\_ServicePointTable Field</span></span>](s_servicepointtable.md)
* [<span data-ttu-id="0a39c-150">Campo System .net. TlsStream. m_Worker</span><span class="sxs-lookup"><span data-stu-id="0a39c-150">System.Net.TlsStream.m_Worker Field</span></span>](system.net.tlsstream.m_worker.md)
* [<span data-ttu-id="0a39c-151">Propriedade System .net. Security. SslState. SslProtocol</span><span class="sxs-lookup"><span data-stu-id="0a39c-151">System.Net.Security.SslState.SslProtocol Property</span></span>](system.net.security.sslstate.sslprotocol.md)
* [<span data-ttu-id="0a39c-152">System. Windows. Diagnostics. VisualDiagnostics. s\_campo isDebuggerCheckDisabledForTestPurposes</span><span class="sxs-lookup"><span data-stu-id="0a39c-152">System.Windows.Diagnostics.VisualDiagnostics.s\_isDebuggerCheckDisabledForTestPurposes Field</span></span>](s-isdebuggercheckdisabledfortestpurposes-field.md)
* [<span data-ttu-id="0a39c-153">Classe System. Windows. Forms. Design. DataMemberFieldEditor</span><span class="sxs-lookup"><span data-stu-id="0a39c-153">System.Windows.Forms.Design.DataMemberFieldEditor Class</span></span>](datamemberfieldeditor-class.md)
* [<span data-ttu-id="0a39c-154">Classe System. Windows. Forms. Design. DataMemberListEditor</span><span class="sxs-lookup"><span data-stu-id="0a39c-154">System.Windows.Forms.Design.DataMemberListEditor Class</span></span>](datamemberlisteditor-class.md)
* [<span data-ttu-id="0a39c-155">Método System. xml. XmlReader. CreateSqlReader</span><span class="sxs-lookup"><span data-stu-id="0a39c-155">System.Xml.XmlReader.CreateSqlReader Method</span></span>](system.xml.xmlreader.createsqlreader.md)
* [<span data-ttu-id="0a39c-156">ActiveX. Interface de conexão</span><span class="sxs-lookup"><span data-stu-id="0a39c-156">adodb.Connection Interface</span></span>](adodb.connection.md)
* [<span data-ttu-id="0a39c-157">ActiveX. EventReason enum</span><span class="sxs-lookup"><span data-stu-id="0a39c-157">adodb.EventReason Enum</span></span>](adodb.eventreasonenum.md)
* [<span data-ttu-id="0a39c-158">ActiveX. EventStatus enum</span><span class="sxs-lookup"><span data-stu-id="0a39c-158">adodb.EventStatus Enum</span></span>](adodb.eventstatusenum.md)
* [<span data-ttu-id="0a39c-159">stdole. Estrutura DISPPARAMS</span><span class="sxs-lookup"><span data-stu-id="0a39c-159">stdole.DISPPARAMS Structure</span></span>](stdole.dispparams.md)
* [<span data-ttu-id="0a39c-160">stdole. Estrutura EXCEPINFO</span><span class="sxs-lookup"><span data-stu-id="0a39c-160">stdole.EXCEPINFO Structure</span></span>](stdole.excepinfo.md)
* [<span data-ttu-id="0a39c-161">stdole. Propriedade IFont.Name</span><span class="sxs-lookup"><span data-stu-id="0a39c-161">stdole.IFont.Name Property</span></span>](stdole.ifont.name.md)
* [<span data-ttu-id="0a39c-162">stdole. Interface IFontDisp</span><span class="sxs-lookup"><span data-stu-id="0a39c-162">stdole.IFontDisp Interface</span></span>](stdole.ifontdisp.md)
* [<span data-ttu-id="0a39c-163">stdole. Propriedade IPicture. Handle</span><span class="sxs-lookup"><span data-stu-id="0a39c-163">stdole.IPicture.Handle Property</span></span>](stdole.ipicture.handle.md)
* [<span data-ttu-id="0a39c-164">stdole. Propriedade IPictureDisp. Handle</span><span class="sxs-lookup"><span data-stu-id="0a39c-164">stdole.IPictureDisp.Handle Property</span></span>](stdole.ipicturedisp.handle.md)
* [<span data-ttu-id="0a39c-165">stdole. Interface StdFont</span><span class="sxs-lookup"><span data-stu-id="0a39c-165">stdole.StdFont Interface</span></span>](stdole.stdfont.md)
* [<span data-ttu-id="0a39c-166">stdole. Interface StdPicture</span><span class="sxs-lookup"><span data-stu-id="0a39c-166">stdole.StdPicture Interface</span></span>](stdole.stdpicture.md)
  
## <a name="see-also"></a><span data-ttu-id="0a39c-167">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0a39c-167">See also</span></span>

* [<span data-ttu-id="0a39c-168">O .NET Framework e lançamentos fora da banda</span><span class="sxs-lookup"><span data-stu-id="0a39c-168">The .NET Framework and Out-of-Band Releases</span></span>](../get-started/the-net-framework-and-out-of-band-releases.md)
