---
title: <chunkedCookieHandler>
ms.date: 03/30/2017
ms.assetid: 7220de45-1d14-4aec-a29e-4a2ea8ac861f
author: BrucePerlerMS
ms.openlocfilehash: d9c81d5de7bea343f0d67fa00037763fbae7b8c5
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59120777"
---
# <a name="chunkedcookiehandler"></a><span data-ttu-id="f3ca4-101">\<chunkedCookieHandler></span><span class="sxs-lookup"><span data-stu-id="f3ca4-101">\<chunkedCookieHandler></span></span>
<span data-ttu-id="f3ca4-102">Configura o <xref:System.IdentityModel.Services.ChunkedCookieHandler>.</span><span class="sxs-lookup"><span data-stu-id="f3ca4-102">Configures the <xref:System.IdentityModel.Services.ChunkedCookieHandler>.</span></span> <span data-ttu-id="f3ca4-103">Esse elemento pode estar presente apenas se o `mode` atributo do `<cookieHandler>` elemento é "Default" ou "Em bloco".</span><span class="sxs-lookup"><span data-stu-id="f3ca4-103">This element may only be present if the `mode` attribute of the `<cookieHandler>` element is "Default" or "Chunked".</span></span>  
  
 <span data-ttu-id="f3ca4-104">\<system.identityModel.services></span><span class="sxs-lookup"><span data-stu-id="f3ca4-104">\<system.identityModel.services></span></span>  
<span data-ttu-id="f3ca4-105">\<federationConfiguration></span><span class="sxs-lookup"><span data-stu-id="f3ca4-105">\<federationConfiguration></span></span>  
<span data-ttu-id="f3ca4-106">\<cookieHandler></span><span class="sxs-lookup"><span data-stu-id="f3ca4-106">\<cookieHandler></span></span>  
<span data-ttu-id="f3ca4-107">\<chunkedCookieHandler></span><span class="sxs-lookup"><span data-stu-id="f3ca4-107">\<chunkedCookieHandler></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f3ca4-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f3ca4-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f3ca4-109">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="f3ca4-109">Attributes and Elements</span></span>  
 <span data-ttu-id="f3ca4-110">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="f3ca4-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f3ca4-111">Atributos</span><span class="sxs-lookup"><span data-stu-id="f3ca4-111">Attributes</span></span>  
  
|<span data-ttu-id="f3ca4-112">Atributo</span><span class="sxs-lookup"><span data-stu-id="f3ca4-112">Attribute</span></span>|<span data-ttu-id="f3ca4-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="f3ca4-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="f3ca4-114">chunkSize</span><span class="sxs-lookup"><span data-stu-id="f3ca4-114">chunkSize</span></span>|<span data-ttu-id="f3ca4-115">O tamanho máximo, em caracteres, dos dados para qualquer cookie HTTP um cookie HTTP.</span><span class="sxs-lookup"><span data-stu-id="f3ca4-115">The maximum size, in characters, of the HTTP cookie data for any one HTTP cookie.</span></span> <span data-ttu-id="f3ca4-116">Você deve ter cuidado ao ajustar o tamanho da parte.</span><span class="sxs-lookup"><span data-stu-id="f3ca4-116">You must be careful when adjusting the chunk size.</span></span> <span data-ttu-id="f3ca4-117">Navegadores da Web têm diferentes limites no tamanho dos cookies e o número permitido por domínio.</span><span class="sxs-lookup"><span data-stu-id="f3ca4-117">Web browsers have different limits on the size of cookies and number allowed per domain.</span></span> <span data-ttu-id="f3ca4-118">Por exemplo, a especificação original do Netscape estipulados esses limites: total de 300 cookies, 4096 bytes por cabeçalho de cookie (incluindo metadados, não apenas o valor do cookie) e 20 cookies por domínio.</span><span class="sxs-lookup"><span data-stu-id="f3ca4-118">For example, the original Netscape specification stipulated these limits: 300 cookies total, 4096 bytes per cookie header (including metadata, not just the cookie value), and 20 cookies per domain.</span></span> <span data-ttu-id="f3ca4-119">O padrão é 2000.</span><span class="sxs-lookup"><span data-stu-id="f3ca4-119">The default is 2000.</span></span> <span data-ttu-id="f3ca4-120">Necessário.</span><span class="sxs-lookup"><span data-stu-id="f3ca4-120">Required.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f3ca4-121">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="f3ca4-121">Child Elements</span></span>  
 <span data-ttu-id="f3ca4-122">Nenhum</span><span class="sxs-lookup"><span data-stu-id="f3ca4-122">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="f3ca4-123">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="f3ca4-123">Parent Elements</span></span>  
  
|<span data-ttu-id="f3ca4-124">Elemento</span><span class="sxs-lookup"><span data-stu-id="f3ca4-124">Element</span></span>|<span data-ttu-id="f3ca4-125">Descrição</span><span class="sxs-lookup"><span data-stu-id="f3ca4-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f3ca4-126">\<cookieHandler></span><span class="sxs-lookup"><span data-stu-id="f3ca4-126">\<cookieHandler></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/cookiehandler.md)|<span data-ttu-id="f3ca4-127">Configura a <xref:System.IdentityModel.Services.CookieHandler> que o <xref:System.IdentityModel.Services.SessionAuthenticationModule> (SAM) usa para ler e gravar cookies.</span><span class="sxs-lookup"><span data-stu-id="f3ca4-127">Configures the <xref:System.IdentityModel.Services.CookieHandler> that the <xref:System.IdentityModel.Services.SessionAuthenticationModule> (SAM) uses to read and write cookies.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f3ca4-128">Comentários</span><span class="sxs-lookup"><span data-stu-id="f3ca4-128">Remarks</span></span>  
 <span data-ttu-id="f3ca4-129">Quando você especifica um <xref:System.IdentityModel.Services.ChunkedCookieHandler> definindo o `mode` atributo da `<cookieHandler>` elemento "Padrão" ou "Em bloco", você pode especificar o tamanho da parte que o manipulador de cookie usa para ler e gravar cookies, incluindo um `<chunkedCookieHandler>` elemento filho e definindo seu `chunkSize` atributo.</span><span class="sxs-lookup"><span data-stu-id="f3ca4-129">When you specify a <xref:System.IdentityModel.Services.ChunkedCookieHandler> by setting the `mode` attribute of the `<cookieHandler>` element to "Default" or "Chunked", you can specify the chunk size that the cookie handler uses to read and write cookies by including a `<chunkedCookieHandler>` child element and setting its `chunkSize` attribute.</span></span> <span data-ttu-id="f3ca4-130">Se o `<chunkedCookieHandler>` elemento não estiver presente, o tamanho da parte padrão de 2.000 bytes é usado.</span><span class="sxs-lookup"><span data-stu-id="f3ca4-130">If the `<chunkedCookieHandler>` element is not present, the default chunk size of 2000 bytes is used.</span></span> <span data-ttu-id="f3ca4-131">Esse elemento não pode ser especificado quando o `mode` atributo é definido como "Custom".</span><span class="sxs-lookup"><span data-stu-id="f3ca4-131">This element cannot be specified when the `mode` attribute is set to "Custom".</span></span>  
  
 <span data-ttu-id="f3ca4-132">O `<chunkedCookieHandler>` elemento é representado pelo <xref:System.IdentityModel.Services.ChunkedCookieHandlerElement> classe.</span><span class="sxs-lookup"><span data-stu-id="f3ca4-132">The `<chunkedCookieHandler>` element is represented by the <xref:System.IdentityModel.Services.ChunkedCookieHandlerElement> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f3ca4-133">Exemplo</span><span class="sxs-lookup"><span data-stu-id="f3ca4-133">Example</span></span>  
 <span data-ttu-id="f3ca4-134">O exemplo a seguir configura um manipulador de cookie em partes que grava os cookies em blocos de 3000 bytes.</span><span class="sxs-lookup"><span data-stu-id="f3ca4-134">The following example configures a chunked cookie handler that writes cookies in chunks of 3000 bytes.</span></span>  
  
```xml  
<cookieHandler mode="Chunked">  
    <chunkedCookieHandler chunkSize=3000/>  
</cookieHandler>  
```  
  
## <a name="see-also"></a><span data-ttu-id="f3ca4-135">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f3ca4-135">See also</span></span>

- <xref:System.IdentityModel.Services.ChunkedCookieHandler>
