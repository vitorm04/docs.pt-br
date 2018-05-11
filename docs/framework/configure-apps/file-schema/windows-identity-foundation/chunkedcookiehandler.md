---
title: '&lt;chunkedCookieHandler&gt;'
ms.date: 03/30/2017
ms.assetid: 7220de45-1d14-4aec-a29e-4a2ea8ac861f
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 193b783e44fe4386d3575e180dc5baa6a7f9a8be
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
---
# <a name="ltchunkedcookiehandlergt"></a><span data-ttu-id="447b1-102">&lt;chunkedCookieHandler&gt;</span><span class="sxs-lookup"><span data-stu-id="447b1-102">&lt;chunkedCookieHandler&gt;</span></span>
<span data-ttu-id="447b1-103">Configura o <xref:System.IdentityModel.Services.ChunkedCookieHandler>.</span><span class="sxs-lookup"><span data-stu-id="447b1-103">Configures the <xref:System.IdentityModel.Services.ChunkedCookieHandler>.</span></span> <span data-ttu-id="447b1-104">Esse elemento só pode estar presente se a `mode` atributo do `<cookieHandler>` elemento é "Padrão" ou "Blocos".</span><span class="sxs-lookup"><span data-stu-id="447b1-104">This element may only be present if the `mode` attribute of the `<cookieHandler>` element is "Default" or "Chunked".</span></span>  
  
 <span data-ttu-id="447b1-105">\<System ></span><span class="sxs-lookup"><span data-stu-id="447b1-105">\<system.identityModel.services></span></span>  
<span data-ttu-id="447b1-106">\<federationConfiguration ></span><span class="sxs-lookup"><span data-stu-id="447b1-106">\<federationConfiguration></span></span>  
<span data-ttu-id="447b1-107">\<cookieHandler ></span><span class="sxs-lookup"><span data-stu-id="447b1-107">\<cookieHandler></span></span>  
<span data-ttu-id="447b1-108">\<chunkedCookieHandler ></span><span class="sxs-lookup"><span data-stu-id="447b1-108">\<chunkedCookieHandler></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="447b1-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="447b1-109">Syntax</span></span>  
  
```xml  
<system.identityModel.services>  
  <federationConfiguration>  
    <cookieHandler mode="Chunked||Default" >  
      <chunkedCookieHandler size=xs:int >  
      </chunkedCookieHandler>  
    </cookieHandler>  
  </federationConfiguration>  
</system.identityModel.services>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="447b1-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="447b1-110">Attributes and Elements</span></span>  
 <span data-ttu-id="447b1-111">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="447b1-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="447b1-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="447b1-112">Attributes</span></span>  
  
|<span data-ttu-id="447b1-113">Atributo</span><span class="sxs-lookup"><span data-stu-id="447b1-113">Attribute</span></span>|<span data-ttu-id="447b1-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="447b1-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="447b1-115">tamanho máximo permitido</span><span class="sxs-lookup"><span data-stu-id="447b1-115">chunkSize</span></span>|<span data-ttu-id="447b1-116">O tamanho máximo, em caracteres, os dados de cookie HTTP para qualquer um cookie HTTP.</span><span class="sxs-lookup"><span data-stu-id="447b1-116">The maximum size, in characters, of the HTTP cookie data for any one HTTP cookie.</span></span> <span data-ttu-id="447b1-117">Você deve ter cuidado ao ajustar o tamanho da parte.</span><span class="sxs-lookup"><span data-stu-id="447b1-117">You must be careful when adjusting the chunk size.</span></span> <span data-ttu-id="447b1-118">Navegadores da Web têm limites diferentes para o tamanho de cookies e o número permitido por domínio.</span><span class="sxs-lookup"><span data-stu-id="447b1-118">Web browsers have different limits on the size of cookies and number allowed per domain.</span></span> <span data-ttu-id="447b1-119">Por exemplo, a especificação de Netscape original estipulado esses limites: total de 300 cookies, 4096 bytes por cabeçalho de cookie (incluindo metadados, não apenas o valor do cookie) e 20 cookies por domínio.</span><span class="sxs-lookup"><span data-stu-id="447b1-119">For example, the original Netscape specification stipulated these limits: 300 cookies total, 4096 bytes per cookie header (including metadata, not just the cookie value), and 20 cookies per domain.</span></span> <span data-ttu-id="447b1-120">O padrão é 2000.</span><span class="sxs-lookup"><span data-stu-id="447b1-120">The default is 2000.</span></span> <span data-ttu-id="447b1-121">Necessário.</span><span class="sxs-lookup"><span data-stu-id="447b1-121">Required.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="447b1-122">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="447b1-122">Child Elements</span></span>  
 <span data-ttu-id="447b1-123">Nenhum</span><span class="sxs-lookup"><span data-stu-id="447b1-123">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="447b1-124">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="447b1-124">Parent Elements</span></span>  
  
|<span data-ttu-id="447b1-125">Elemento</span><span class="sxs-lookup"><span data-stu-id="447b1-125">Element</span></span>|<span data-ttu-id="447b1-126">Descrição</span><span class="sxs-lookup"><span data-stu-id="447b1-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="447b1-127">\<cookieHandler ></span><span class="sxs-lookup"><span data-stu-id="447b1-127">\<cookieHandler></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/cookiehandler.md)|<span data-ttu-id="447b1-128">Configura o <xref:System.IdentityModel.Services.CookieHandler> que o <xref:System.IdentityModel.Services.SessionAuthenticationModule> (SAM) usa para ler e gravar cookies.</span><span class="sxs-lookup"><span data-stu-id="447b1-128">Configures the <xref:System.IdentityModel.Services.CookieHandler> that the <xref:System.IdentityModel.Services.SessionAuthenticationModule> (SAM) uses to read and write cookies.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="447b1-129">Comentários</span><span class="sxs-lookup"><span data-stu-id="447b1-129">Remarks</span></span>  
 <span data-ttu-id="447b1-130">Quando você especifica um <xref:System.IdentityModel.Services.ChunkedCookieHandler> definindo o `mode` atributo do `<cookieHandler>` elemento "Padrão" ou "Em partes", você pode especificar o tamanho da parte que usa o manipulador de cookie para ler e gravar cookies, incluindo um `<chunkedCookieHandler>` elemento filho e Configurando seu `chunkSize` atributo.</span><span class="sxs-lookup"><span data-stu-id="447b1-130">When you specify a <xref:System.IdentityModel.Services.ChunkedCookieHandler> by setting the `mode` attribute of the `<cookieHandler>` element to "Default" or "Chunked", you can specify the chunk size that the cookie handler uses to read and write cookies by including a `<chunkedCookieHandler>` child element and setting its `chunkSize` attribute.</span></span> <span data-ttu-id="447b1-131">Se o `<chunkedCookieHandler>` elemento não estiver presente, o tamanho da parte padrão de bytes 2000 é usado.</span><span class="sxs-lookup"><span data-stu-id="447b1-131">If the `<chunkedCookieHandler>` element is not present, the default chunk size of 2000 bytes is used.</span></span> <span data-ttu-id="447b1-132">Esse elemento não pode ser especificado quando o `mode` atributo é definido como "Custom".</span><span class="sxs-lookup"><span data-stu-id="447b1-132">This element cannot be specified when the `mode` attribute is set to "Custom".</span></span>  
  
 <span data-ttu-id="447b1-133">O `<chunkedCookieHandler>` elemento é representado pela <xref:System.IdentityModel.Services.ChunkedCookieHandlerElement> classe.</span><span class="sxs-lookup"><span data-stu-id="447b1-133">The `<chunkedCookieHandler>` element is represented by the <xref:System.IdentityModel.Services.ChunkedCookieHandlerElement> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="447b1-134">Exemplo</span><span class="sxs-lookup"><span data-stu-id="447b1-134">Example</span></span>  
 <span data-ttu-id="447b1-135">O exemplo a seguir configura um manipulador de cookie em partes que grava cookies em blocos de 3000 bytes.</span><span class="sxs-lookup"><span data-stu-id="447b1-135">The following example configures a chunked cookie handler that writes cookies in chunks of 3000 bytes.</span></span>  
  
```xml  
<cookieHandler mode="Chunked">  
    <chunkedCookieHandler chunkSize=3000/>  
</cookieHandler>  
```  
  
## <a name="see-also"></a><span data-ttu-id="447b1-136">Consulte também</span><span class="sxs-lookup"><span data-stu-id="447b1-136">See Also</span></span>  
 <xref:System.IdentityModel.Services.ChunkedCookieHandler>
