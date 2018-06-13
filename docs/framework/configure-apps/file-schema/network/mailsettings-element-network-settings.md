---
title: '&lt;mailSettings&gt; elemento (configurações de rede)'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#mailSettings
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/mailSettings
helpviewer_keywords:
- mailSettings element
- <mailSettings> element
ms.assetid: 54f0f153-17e5-4f49-afdc-deadb940c9c1
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 5bc7cc649b18a5330d056bbddfe96db4ecca2ec8
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32746417"
---
# <a name="ltmailsettingsgt-element-network-settings"></a><span data-ttu-id="d6e57-102">&lt;mailSettings&gt; elemento (configurações de rede)</span><span class="sxs-lookup"><span data-stu-id="d6e57-102">&lt;mailSettings&gt; Element (Network Settings)</span></span>
<span data-ttu-id="d6e57-103">Configura as opções de envio de email.</span><span class="sxs-lookup"><span data-stu-id="d6e57-103">Configures mail sending options.</span></span>  

<span data-ttu-id="d6e57-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="d6e57-104">\<configuration></span></span>  
<span data-ttu-id="d6e57-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="d6e57-105">\<system.net></span></span>  
<span data-ttu-id="d6e57-106">\<mailSettings></span><span class="sxs-lookup"><span data-stu-id="d6e57-106">\<mailSettings></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d6e57-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d6e57-107">Syntax</span></span>  
  
```xml  
<mailSettings>
  <smtp> … </smtp>  
</mailSettings>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d6e57-108">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="d6e57-108">Attributes and Elements</span></span>  
 <span data-ttu-id="d6e57-109">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="d6e57-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d6e57-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="d6e57-110">Attributes</span></span>  
 <span data-ttu-id="d6e57-111">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="d6e57-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="d6e57-112">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="d6e57-112">Child Elements</span></span>  
  
|<span data-ttu-id="d6e57-113">Atributo</span><span class="sxs-lookup"><span data-stu-id="d6e57-113">Attribute</span></span>|<span data-ttu-id="d6e57-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="d6e57-114">Description</span></span>|  
|---------------|-----------------|  
|[<span data-ttu-id="d6e57-115">\<SMTP > elemento (configurações de rede)</span><span class="sxs-lookup"><span data-stu-id="d6e57-115">\<smtp> Element (Network Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/smtp-element-network-settings.md)|<span data-ttu-id="d6e57-116">Configura as opções de Simple Mail Transport Protocol.</span><span class="sxs-lookup"><span data-stu-id="d6e57-116">Configures Simple Mail Transport Protocol options.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="d6e57-117">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="d6e57-117">Parent Elements</span></span>  
  
|<span data-ttu-id="d6e57-118">**Elemento**</span><span class="sxs-lookup"><span data-stu-id="d6e57-118">**Element**</span></span>|<span data-ttu-id="d6e57-119">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="d6e57-119">**Description**</span></span>|  
|-----------------|---------------------|  
|<span data-ttu-id="d6e57-120">Elemento [\<system.Net> (configurações de rede)](../../../../../docs/framework/configure-apps/file-schema/network/system-net-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="d6e57-120">[\<system.Net> Element (Network Settings)](../../../../../docs/framework/configure-apps/file-schema/network/system-net-element-network-settings.md)</span></span>|<span data-ttu-id="d6e57-121">Contém configurações que especificam como o .NET Framework se conecta à rede.</span><span class="sxs-lookup"><span data-stu-id="d6e57-121">Contains settings that specify how the .NET Framework connects to the network.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="d6e57-122">Exemplo</span><span class="sxs-lookup"><span data-stu-id="d6e57-122">Example</span></span>  
 <span data-ttu-id="d6e57-123">O exemplo a seguir especifica os parâmetros apropriados de SMTP para enviar email usando as credenciais de rede padrão.</span><span class="sxs-lookup"><span data-stu-id="d6e57-123">The following example specifies the appropriate SMTP parameters to send email using the default network credentials.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="d6e57-124">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d6e57-124">See Also</span></span>  
 <xref:System.Net.Mail.SmtpClient>  
 [<span data-ttu-id="d6e57-125">Esquema de configurações de rede</span><span class="sxs-lookup"><span data-stu-id="d6e57-125">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
