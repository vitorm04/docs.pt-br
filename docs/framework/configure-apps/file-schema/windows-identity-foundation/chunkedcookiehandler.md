---
title: <chunkedCookieHandler>
ms.date: 03/30/2017
ms.assetid: 7220de45-1d14-4aec-a29e-4a2ea8ac861f
author: BrucePerlerMS
ms.openlocfilehash: a321c10e04eca2c1a5204929966a1725e918cbdf
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91158520"
---
# \<chunkedCookieHandler>

<span data-ttu-id="dea6b-101">Configura o <xref:System.IdentityModel.Services.ChunkedCookieHandler> .</span><span class="sxs-lookup"><span data-stu-id="dea6b-101">Configures the <xref:System.IdentityModel.Services.ChunkedCookieHandler>.</span></span> <span data-ttu-id="dea6b-102">Esse elemento só poderá estar presente se o `mode` atributo do `<cookieHandler>` elemento for "padrão" ou "em bloco".</span><span class="sxs-lookup"><span data-stu-id="dea6b-102">This element may only be present if the `mode` attribute of the `<cookieHandler>` element is "Default" or "Chunked".</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel.services>**](system-identitymodel-services.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<federationConfiguration>**](federationconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<cookieHandler>**](cookiehandler.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<chunkedCookieHandler>**  
  
## <a name="syntax"></a><span data-ttu-id="dea6b-103">Syntax</span><span class="sxs-lookup"><span data-stu-id="dea6b-103">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="dea6b-104">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="dea6b-104">Attributes and Elements</span></span>  

 <span data-ttu-id="dea6b-105">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="dea6b-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="dea6b-106">Atributos</span><span class="sxs-lookup"><span data-stu-id="dea6b-106">Attributes</span></span>  
  
|<span data-ttu-id="dea6b-107">Atributo</span><span class="sxs-lookup"><span data-stu-id="dea6b-107">Attribute</span></span>|<span data-ttu-id="dea6b-108">Descrição</span><span class="sxs-lookup"><span data-stu-id="dea6b-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="dea6b-109">chunkSize</span><span class="sxs-lookup"><span data-stu-id="dea6b-109">chunkSize</span></span>|<span data-ttu-id="dea6b-110">O tamanho máximo, em caracteres, dos dados do cookie HTTP para qualquer cookie HTTP.</span><span class="sxs-lookup"><span data-stu-id="dea6b-110">The maximum size, in characters, of the HTTP cookie data for any one HTTP cookie.</span></span> <span data-ttu-id="dea6b-111">Você deve ter cuidado ao ajustar o tamanho da parte.</span><span class="sxs-lookup"><span data-stu-id="dea6b-111">You must be careful when adjusting the chunk size.</span></span> <span data-ttu-id="dea6b-112">Os navegadores da Web têm limites diferentes no tamanho dos cookies e do número permitido por domínio.</span><span class="sxs-lookup"><span data-stu-id="dea6b-112">Web browsers have different limits on the size of cookies and number allowed per domain.</span></span> <span data-ttu-id="dea6b-113">Por exemplo, a especificação original do Netscape estipulava esses limites: 300 cookies totais, 4096 bytes por cabeçalho de cookie (incluindo metadados, não apenas o valor de cookie) e 20 cookies por domínio.</span><span class="sxs-lookup"><span data-stu-id="dea6b-113">For example, the original Netscape specification stipulated these limits: 300 cookies total, 4096 bytes per cookie header (including metadata, not just the cookie value), and 20 cookies per domain.</span></span> <span data-ttu-id="dea6b-114">O padrão é 2000.</span><span class="sxs-lookup"><span data-stu-id="dea6b-114">The default is 2000.</span></span> <span data-ttu-id="dea6b-115">Necessário.</span><span class="sxs-lookup"><span data-stu-id="dea6b-115">Required.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="dea6b-116">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="dea6b-116">Child Elements</span></span>  

 <span data-ttu-id="dea6b-117">Nenhum</span><span class="sxs-lookup"><span data-stu-id="dea6b-117">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="dea6b-118">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="dea6b-118">Parent Elements</span></span>  
  
|<span data-ttu-id="dea6b-119">Elemento</span><span class="sxs-lookup"><span data-stu-id="dea6b-119">Element</span></span>|<span data-ttu-id="dea6b-120">Descrição</span><span class="sxs-lookup"><span data-stu-id="dea6b-120">Description</span></span>|  
|-------------|-----------------|  
|[\<cookieHandler>](cookiehandler.md)|<span data-ttu-id="dea6b-121">Configura o <xref:System.IdentityModel.Services.CookieHandler> que o <xref:System.IdentityModel.Services.SessionAuthenticationModule> (Sam) usa para ler e gravar cookies.</span><span class="sxs-lookup"><span data-stu-id="dea6b-121">Configures the <xref:System.IdentityModel.Services.CookieHandler> that the <xref:System.IdentityModel.Services.SessionAuthenticationModule> (SAM) uses to read and write cookies.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="dea6b-122">Comentários</span><span class="sxs-lookup"><span data-stu-id="dea6b-122">Remarks</span></span>  

 <span data-ttu-id="dea6b-123">Ao especificar um <xref:System.IdentityModel.Services.ChunkedCookieHandler> definindo o `mode` atributo do `<cookieHandler>` elemento como "padrão" ou "em bloco", você pode especificar o tamanho da parte que o manipulador de cookies usa para ler e gravar cookies, incluindo um `<chunkedCookieHandler>` elemento filho e definindo seu `chunkSize` atributo.</span><span class="sxs-lookup"><span data-stu-id="dea6b-123">When you specify a <xref:System.IdentityModel.Services.ChunkedCookieHandler> by setting the `mode` attribute of the `<cookieHandler>` element to "Default" or "Chunked", you can specify the chunk size that the cookie handler uses to read and write cookies by including a `<chunkedCookieHandler>` child element and setting its `chunkSize` attribute.</span></span> <span data-ttu-id="dea6b-124">Se o `<chunkedCookieHandler>` elemento não estiver presente, o tamanho de bloco padrão de 2000 bytes será usado.</span><span class="sxs-lookup"><span data-stu-id="dea6b-124">If the `<chunkedCookieHandler>` element is not present, the default chunk size of 2000 bytes is used.</span></span> <span data-ttu-id="dea6b-125">Este elemento não pode ser especificado quando o `mode` atributo está definido como "Custom".</span><span class="sxs-lookup"><span data-stu-id="dea6b-125">This element cannot be specified when the `mode` attribute is set to "Custom".</span></span>  
  
 <span data-ttu-id="dea6b-126">O `<chunkedCookieHandler>` elemento é representado pela <xref:System.IdentityModel.Services.ChunkedCookieHandlerElement> classe.</span><span class="sxs-lookup"><span data-stu-id="dea6b-126">The `<chunkedCookieHandler>` element is represented by the <xref:System.IdentityModel.Services.ChunkedCookieHandlerElement> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="dea6b-127">Exemplo</span><span class="sxs-lookup"><span data-stu-id="dea6b-127">Example</span></span>  

 <span data-ttu-id="dea6b-128">O exemplo a seguir configura um manipulador de cookie em bloco que grava cookies em partes de 3000 bytes.</span><span class="sxs-lookup"><span data-stu-id="dea6b-128">The following example configures a chunked cookie handler that writes cookies in chunks of 3000 bytes.</span></span>  
  
```xml  
<cookieHandler mode="Chunked">  
    <chunkedCookieHandler chunkSize=3000/>  
</cookieHandler>  
```  
  
## <a name="see-also"></a><span data-ttu-id="dea6b-129">Confira também</span><span class="sxs-lookup"><span data-stu-id="dea6b-129">See also</span></span>

- <xref:System.IdentityModel.Services.ChunkedCookieHandler>
