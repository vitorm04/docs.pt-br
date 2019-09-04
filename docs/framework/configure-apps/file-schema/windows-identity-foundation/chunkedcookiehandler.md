---
title: <chunkedCookieHandler>
ms.date: 03/30/2017
ms.assetid: 7220de45-1d14-4aec-a29e-4a2ea8ac861f
author: BrucePerlerMS
ms.openlocfilehash: 6aad95033b99f1472284f838f3ede2e74ea8324c
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70252103"
---
# <a name="chunkedcookiehandler"></a><span data-ttu-id="8c843-101">\<chunkedCookieHandler></span><span class="sxs-lookup"><span data-stu-id="8c843-101">\<chunkedCookieHandler></span></span>
<span data-ttu-id="8c843-102">Configura o <xref:System.IdentityModel.Services.ChunkedCookieHandler>.</span><span class="sxs-lookup"><span data-stu-id="8c843-102">Configures the <xref:System.IdentityModel.Services.ChunkedCookieHandler>.</span></span> <span data-ttu-id="8c843-103">Esse elemento só poderá estar presente se o `mode` atributo `<cookieHandler>` do elemento for "padrão" ou "em bloco".</span><span class="sxs-lookup"><span data-stu-id="8c843-103">This element may only be present if the `mode` attribute of the `<cookieHandler>` element is "Default" or "Chunked".</span></span>  
  
<span data-ttu-id="8c843-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="8c843-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="8c843-105">&nbsp;&nbsp;[ **\<System. identityModel. Services >** ](system-identitymodel-services.md)</span><span class="sxs-lookup"><span data-stu-id="8c843-105">&nbsp;&nbsp;[**\<system.identityModel.services>**](system-identitymodel-services.md)</span></span>\
<span data-ttu-id="8c843-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> federationConfiguration**](federationconfiguration.md)</span><span class="sxs-lookup"><span data-stu-id="8c843-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<federationConfiguration>**](federationconfiguration.md)</span></span>\
<span data-ttu-id="8c843-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> cookieHandler**](cookiehandler.md)</span><span class="sxs-lookup"><span data-stu-id="8c843-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<cookieHandler>**](cookiehandler.md)</span></span>\
<span data-ttu-id="8c843-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> chunkedCookieHandler**</span><span class="sxs-lookup"><span data-stu-id="8c843-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<chunkedCookieHandler>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8c843-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="8c843-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8c843-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="8c843-110">Attributes and Elements</span></span>  
 <span data-ttu-id="8c843-111">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="8c843-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8c843-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="8c843-112">Attributes</span></span>  
  
|<span data-ttu-id="8c843-113">Atributo</span><span class="sxs-lookup"><span data-stu-id="8c843-113">Attribute</span></span>|<span data-ttu-id="8c843-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="8c843-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="8c843-115">chunkSize</span><span class="sxs-lookup"><span data-stu-id="8c843-115">chunkSize</span></span>|<span data-ttu-id="8c843-116">O tamanho máximo, em caracteres, dos dados do cookie HTTP para qualquer cookie HTTP.</span><span class="sxs-lookup"><span data-stu-id="8c843-116">The maximum size, in characters, of the HTTP cookie data for any one HTTP cookie.</span></span> <span data-ttu-id="8c843-117">Você deve ter cuidado ao ajustar o tamanho da parte.</span><span class="sxs-lookup"><span data-stu-id="8c843-117">You must be careful when adjusting the chunk size.</span></span> <span data-ttu-id="8c843-118">Os navegadores da Web têm limites diferentes no tamanho dos cookies e do número permitido por domínio.</span><span class="sxs-lookup"><span data-stu-id="8c843-118">Web browsers have different limits on the size of cookies and number allowed per domain.</span></span> <span data-ttu-id="8c843-119">Por exemplo, a especificação original do Netscape estipulava esses limites: 300 total de cookies, 4096 bytes por cabeçalho de cookie (incluindo metadados, não apenas o valor de cookie) e 20 cookies por domínio.</span><span class="sxs-lookup"><span data-stu-id="8c843-119">For example, the original Netscape specification stipulated these limits: 300 cookies total, 4096 bytes per cookie header (including metadata, not just the cookie value), and 20 cookies per domain.</span></span> <span data-ttu-id="8c843-120">O padrão é 2000.</span><span class="sxs-lookup"><span data-stu-id="8c843-120">The default is 2000.</span></span> <span data-ttu-id="8c843-121">Necessário.</span><span class="sxs-lookup"><span data-stu-id="8c843-121">Required.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="8c843-122">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="8c843-122">Child Elements</span></span>  
 <span data-ttu-id="8c843-123">Nenhum</span><span class="sxs-lookup"><span data-stu-id="8c843-123">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="8c843-124">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="8c843-124">Parent Elements</span></span>  
  
|<span data-ttu-id="8c843-125">Elemento</span><span class="sxs-lookup"><span data-stu-id="8c843-125">Element</span></span>|<span data-ttu-id="8c843-126">Descrição</span><span class="sxs-lookup"><span data-stu-id="8c843-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="8c843-127">\<> cookieHandler</span><span class="sxs-lookup"><span data-stu-id="8c843-127">\<cookieHandler></span></span>](cookiehandler.md)|<span data-ttu-id="8c843-128">Configura o <xref:System.IdentityModel.Services.CookieHandler> que o <xref:System.IdentityModel.Services.SessionAuthenticationModule> (Sam) usa para ler e gravar cookies.</span><span class="sxs-lookup"><span data-stu-id="8c843-128">Configures the <xref:System.IdentityModel.Services.CookieHandler> that the <xref:System.IdentityModel.Services.SessionAuthenticationModule> (SAM) uses to read and write cookies.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8c843-129">Comentários</span><span class="sxs-lookup"><span data-stu-id="8c843-129">Remarks</span></span>  
 <span data-ttu-id="8c843-130">Ao especificar um <xref:System.IdentityModel.Services.ChunkedCookieHandler> definindo o `mode` atributo do `<cookieHandler>` elemento como "padrão" ou "em bloco", você pode especificar o tamanho da parte que o manipulador de cookies usa para ler e gravar cookies, incluindo um `<chunkedCookieHandler>` elemento filho e definindo seu `chunkSize` atributo.</span><span class="sxs-lookup"><span data-stu-id="8c843-130">When you specify a <xref:System.IdentityModel.Services.ChunkedCookieHandler> by setting the `mode` attribute of the `<cookieHandler>` element to "Default" or "Chunked", you can specify the chunk size that the cookie handler uses to read and write cookies by including a `<chunkedCookieHandler>` child element and setting its `chunkSize` attribute.</span></span> <span data-ttu-id="8c843-131">Se o `<chunkedCookieHandler>` elemento não estiver presente, o tamanho de bloco padrão de 2000 bytes será usado.</span><span class="sxs-lookup"><span data-stu-id="8c843-131">If the `<chunkedCookieHandler>` element is not present, the default chunk size of 2000 bytes is used.</span></span> <span data-ttu-id="8c843-132">Este elemento não pode ser especificado quando `mode` o atributo está definido como "Custom".</span><span class="sxs-lookup"><span data-stu-id="8c843-132">This element cannot be specified when the `mode` attribute is set to "Custom".</span></span>  
  
 <span data-ttu-id="8c843-133">O `<chunkedCookieHandler>` elemento é representado <xref:System.IdentityModel.Services.ChunkedCookieHandlerElement> pela classe.</span><span class="sxs-lookup"><span data-stu-id="8c843-133">The `<chunkedCookieHandler>` element is represented by the <xref:System.IdentityModel.Services.ChunkedCookieHandlerElement> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8c843-134">Exemplo</span><span class="sxs-lookup"><span data-stu-id="8c843-134">Example</span></span>  
 <span data-ttu-id="8c843-135">O exemplo a seguir configura um manipulador de cookie em bloco que grava cookies em partes de 3000 bytes.</span><span class="sxs-lookup"><span data-stu-id="8c843-135">The following example configures a chunked cookie handler that writes cookies in chunks of 3000 bytes.</span></span>  
  
```xml  
<cookieHandler mode="Chunked">  
    <chunkedCookieHandler chunkSize=3000/>  
</cookieHandler>  
```  
  
## <a name="see-also"></a><span data-ttu-id="8c843-136">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8c843-136">See also</span></span>

- <xref:System.IdentityModel.Services.ChunkedCookieHandler>
