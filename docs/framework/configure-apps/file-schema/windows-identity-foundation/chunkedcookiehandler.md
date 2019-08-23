---
title: <chunkedCookieHandler>
ms.date: 03/30/2017
ms.assetid: 7220de45-1d14-4aec-a29e-4a2ea8ac861f
author: BrucePerlerMS
ms.openlocfilehash: b3b4cf0d7c2748079af7a94534622b1dbadd3ab5
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69941885"
---
# <a name="chunkedcookiehandler"></a><span data-ttu-id="7804d-101">\<chunkedCookieHandler></span><span class="sxs-lookup"><span data-stu-id="7804d-101">\<chunkedCookieHandler></span></span>
<span data-ttu-id="7804d-102">Configura o <xref:System.IdentityModel.Services.ChunkedCookieHandler>.</span><span class="sxs-lookup"><span data-stu-id="7804d-102">Configures the <xref:System.IdentityModel.Services.ChunkedCookieHandler>.</span></span> <span data-ttu-id="7804d-103">Esse elemento só poderá estar presente se o `mode` atributo `<cookieHandler>` do elemento for "padrão" ou "em bloco".</span><span class="sxs-lookup"><span data-stu-id="7804d-103">This element may only be present if the `mode` attribute of the `<cookieHandler>` element is "Default" or "Chunked".</span></span>  
  
 <span data-ttu-id="7804d-104">\<system.identityModel.services></span><span class="sxs-lookup"><span data-stu-id="7804d-104">\<system.identityModel.services></span></span>  
<span data-ttu-id="7804d-105">\<federationConfiguration></span><span class="sxs-lookup"><span data-stu-id="7804d-105">\<federationConfiguration></span></span>  
<span data-ttu-id="7804d-106">\<> cookieHandler</span><span class="sxs-lookup"><span data-stu-id="7804d-106">\<cookieHandler></span></span>  
<span data-ttu-id="7804d-107">\<chunkedCookieHandler></span><span class="sxs-lookup"><span data-stu-id="7804d-107">\<chunkedCookieHandler></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7804d-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="7804d-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7804d-109">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="7804d-109">Attributes and Elements</span></span>  
 <span data-ttu-id="7804d-110">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="7804d-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7804d-111">Atributos</span><span class="sxs-lookup"><span data-stu-id="7804d-111">Attributes</span></span>  
  
|<span data-ttu-id="7804d-112">Atributo</span><span class="sxs-lookup"><span data-stu-id="7804d-112">Attribute</span></span>|<span data-ttu-id="7804d-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="7804d-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="7804d-114">chunkSize</span><span class="sxs-lookup"><span data-stu-id="7804d-114">chunkSize</span></span>|<span data-ttu-id="7804d-115">O tamanho máximo, em caracteres, dos dados do cookie HTTP para qualquer cookie HTTP.</span><span class="sxs-lookup"><span data-stu-id="7804d-115">The maximum size, in characters, of the HTTP cookie data for any one HTTP cookie.</span></span> <span data-ttu-id="7804d-116">Você deve ter cuidado ao ajustar o tamanho da parte.</span><span class="sxs-lookup"><span data-stu-id="7804d-116">You must be careful when adjusting the chunk size.</span></span> <span data-ttu-id="7804d-117">Os navegadores da Web têm limites diferentes no tamanho dos cookies e do número permitido por domínio.</span><span class="sxs-lookup"><span data-stu-id="7804d-117">Web browsers have different limits on the size of cookies and number allowed per domain.</span></span> <span data-ttu-id="7804d-118">Por exemplo, a especificação original do Netscape estipulava esses limites: 300 total de cookies, 4096 bytes por cabeçalho de cookie (incluindo metadados, não apenas o valor de cookie) e 20 cookies por domínio.</span><span class="sxs-lookup"><span data-stu-id="7804d-118">For example, the original Netscape specification stipulated these limits: 300 cookies total, 4096 bytes per cookie header (including metadata, not just the cookie value), and 20 cookies per domain.</span></span> <span data-ttu-id="7804d-119">O padrão é 2000.</span><span class="sxs-lookup"><span data-stu-id="7804d-119">The default is 2000.</span></span> <span data-ttu-id="7804d-120">Necessário.</span><span class="sxs-lookup"><span data-stu-id="7804d-120">Required.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="7804d-121">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="7804d-121">Child Elements</span></span>  
 <span data-ttu-id="7804d-122">Nenhum</span><span class="sxs-lookup"><span data-stu-id="7804d-122">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="7804d-123">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="7804d-123">Parent Elements</span></span>  
  
|<span data-ttu-id="7804d-124">Elemento</span><span class="sxs-lookup"><span data-stu-id="7804d-124">Element</span></span>|<span data-ttu-id="7804d-125">Descrição</span><span class="sxs-lookup"><span data-stu-id="7804d-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7804d-126">\<> cookieHandler</span><span class="sxs-lookup"><span data-stu-id="7804d-126">\<cookieHandler></span></span>](cookiehandler.md)|<span data-ttu-id="7804d-127">Configura o <xref:System.IdentityModel.Services.CookieHandler> que o <xref:System.IdentityModel.Services.SessionAuthenticationModule> (Sam) usa para ler e gravar cookies.</span><span class="sxs-lookup"><span data-stu-id="7804d-127">Configures the <xref:System.IdentityModel.Services.CookieHandler> that the <xref:System.IdentityModel.Services.SessionAuthenticationModule> (SAM) uses to read and write cookies.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7804d-128">Comentários</span><span class="sxs-lookup"><span data-stu-id="7804d-128">Remarks</span></span>  
 <span data-ttu-id="7804d-129">Ao especificar um <xref:System.IdentityModel.Services.ChunkedCookieHandler> definindo o `mode` atributo do `<cookieHandler>` elemento como "padrão" ou "em bloco", você pode especificar o tamanho da parte que o manipulador de cookies usa para ler e gravar cookies, incluindo um `<chunkedCookieHandler>` elemento filho e definindo seu `chunkSize` atributo.</span><span class="sxs-lookup"><span data-stu-id="7804d-129">When you specify a <xref:System.IdentityModel.Services.ChunkedCookieHandler> by setting the `mode` attribute of the `<cookieHandler>` element to "Default" or "Chunked", you can specify the chunk size that the cookie handler uses to read and write cookies by including a `<chunkedCookieHandler>` child element and setting its `chunkSize` attribute.</span></span> <span data-ttu-id="7804d-130">Se o `<chunkedCookieHandler>` elemento não estiver presente, o tamanho de bloco padrão de 2000 bytes será usado.</span><span class="sxs-lookup"><span data-stu-id="7804d-130">If the `<chunkedCookieHandler>` element is not present, the default chunk size of 2000 bytes is used.</span></span> <span data-ttu-id="7804d-131">Este elemento não pode ser especificado quando `mode` o atributo está definido como "Custom".</span><span class="sxs-lookup"><span data-stu-id="7804d-131">This element cannot be specified when the `mode` attribute is set to "Custom".</span></span>  
  
 <span data-ttu-id="7804d-132">O `<chunkedCookieHandler>` elemento é representado <xref:System.IdentityModel.Services.ChunkedCookieHandlerElement> pela classe.</span><span class="sxs-lookup"><span data-stu-id="7804d-132">The `<chunkedCookieHandler>` element is represented by the <xref:System.IdentityModel.Services.ChunkedCookieHandlerElement> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7804d-133">Exemplo</span><span class="sxs-lookup"><span data-stu-id="7804d-133">Example</span></span>  
 <span data-ttu-id="7804d-134">O exemplo a seguir configura um manipulador de cookie em bloco que grava cookies em partes de 3000 bytes.</span><span class="sxs-lookup"><span data-stu-id="7804d-134">The following example configures a chunked cookie handler that writes cookies in chunks of 3000 bytes.</span></span>  
  
```xml  
<cookieHandler mode="Chunked">  
    <chunkedCookieHandler chunkSize=3000/>  
</cookieHandler>  
```  
  
## <a name="see-also"></a><span data-ttu-id="7804d-135">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7804d-135">See also</span></span>

- <xref:System.IdentityModel.Services.ChunkedCookieHandler>
