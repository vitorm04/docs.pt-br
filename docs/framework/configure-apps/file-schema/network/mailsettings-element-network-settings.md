---
title: "&lt;mailSettings&gt; elemento (configurações de rede)"
ms.date: 03/30/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#mailSettings
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/mailSettings
helpviewer_keywords:
- mailSettings element
- <mailSettings> element
ms.assetid: 54f0f153-17e5-4f49-afdc-deadb940c9c1
caps.latest.revision: "20"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: a42b10574a1f44d310f86fe3fa99490f2f1981c6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="ltmailsettingsgt-element-network-settings"></a><span data-ttu-id="a0a98-102">&lt;mailSettings&gt; elemento (configurações de rede)</span><span class="sxs-lookup"><span data-stu-id="a0a98-102">&lt;mailSettings&gt; Element (Network Settings)</span></span>
<span data-ttu-id="a0a98-103">Configura as opções de envio de email.</span><span class="sxs-lookup"><span data-stu-id="a0a98-103">Configures mail sending options.</span></span>  

<span data-ttu-id="a0a98-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="a0a98-104">\<configuration></span></span>  
<span data-ttu-id="a0a98-105">\<System.NET ></span><span class="sxs-lookup"><span data-stu-id="a0a98-105">\<system.net></span></span>  
<span data-ttu-id="a0a98-106">\<mailSettings ></span><span class="sxs-lookup"><span data-stu-id="a0a98-106">\<mailSettings></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a0a98-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a0a98-107">Syntax</span></span>  
  
```xml  
<mailSettings>
  <smtp> … </smtp>  
</mailSettings>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a0a98-108">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="a0a98-108">Attributes and Elements</span></span>  
 <span data-ttu-id="a0a98-109">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="a0a98-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a0a98-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="a0a98-110">Attributes</span></span>  
 <span data-ttu-id="a0a98-111">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="a0a98-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="a0a98-112">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="a0a98-112">Child Elements</span></span>  
  
|<span data-ttu-id="a0a98-113">Atributo</span><span class="sxs-lookup"><span data-stu-id="a0a98-113">Attribute</span></span>|<span data-ttu-id="a0a98-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="a0a98-114">Description</span></span>|  
|---------------|-----------------|  
|[<span data-ttu-id="a0a98-115">\<SMTP > elemento (configurações de rede)</span><span class="sxs-lookup"><span data-stu-id="a0a98-115">\<smtp> Element (Network Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/smtp-element-network-settings.md)|<span data-ttu-id="a0a98-116">Configura as opções de Simple Mail Transport Protocol.</span><span class="sxs-lookup"><span data-stu-id="a0a98-116">Configures Simple Mail Transport Protocol options.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="a0a98-117">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="a0a98-117">Parent Elements</span></span>  
  
|<span data-ttu-id="a0a98-118">**Elemento**</span><span class="sxs-lookup"><span data-stu-id="a0a98-118">**Element**</span></span>|<span data-ttu-id="a0a98-119">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="a0a98-119">**Description**</span></span>|  
|-----------------|---------------------|  
|<span data-ttu-id="a0a98-120">Elemento [\<system.Net> (configurações de rede)](../../../../../docs/framework/configure-apps/file-schema/network/system-net-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="a0a98-120">[\<system.Net> Element (Network Settings)](../../../../../docs/framework/configure-apps/file-schema/network/system-net-element-network-settings.md)</span></span>|<span data-ttu-id="a0a98-121">Contém configurações que especificam como o .NET Framework se conecta à rede.</span><span class="sxs-lookup"><span data-stu-id="a0a98-121">Contains settings that specify how the .NET Framework connects to the network.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="a0a98-122">Exemplo</span><span class="sxs-lookup"><span data-stu-id="a0a98-122">Example</span></span>  
 <span data-ttu-id="a0a98-123">O exemplo a seguir especifica os parâmetros apropriados de SMTP para enviar email usando as credenciais de rede padrão.</span><span class="sxs-lookup"><span data-stu-id="a0a98-123">The following example specifies the appropriate SMTP parameters to send e-mail using the default network credentials.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <mailSettings>  
      <smtp deliveryMethod="network">  
        <network  
          host="localhost"  
          port="25"  
          defaultCredentials="true"  
        />  
      </smtp>  
    </mailSettings>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="a0a98-124">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a0a98-124">See Also</span></span>  
 <xref:System.Net.Mail.SmtpClient>  
 [<span data-ttu-id="a0a98-125">Esquema de configurações de rede</span><span class="sxs-lookup"><span data-stu-id="a0a98-125">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
