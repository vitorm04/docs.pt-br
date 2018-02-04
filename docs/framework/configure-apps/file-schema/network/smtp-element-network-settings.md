---
title: "&lt;SMTP&gt; elemento (configurações de rede)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/mailSettings/smtp
- http://schemas.microsoft.com/.NetConfiguration/v2.0#smtp
helpviewer_keywords:
- <smtp> element
- smtp element
ms.assetid: 220b0329-e384-4e0c-86b4-0945ad17efd9
caps.latest.revision: 
author: mcleblanc
ms.author: markl
manager: markl
ms.workload:
- dotnet
ms.openlocfilehash: f5b2a3b7eec17fbdd12181c29f610d2b2ad32bd4
ms.sourcegitcommit: cf22b29db780e532e1090c6e755aa52d28273fa6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/01/2018
---
# <a name="ltsmtpgt-element-network-settings"></a><span data-ttu-id="f86dd-102">&lt;SMTP&gt; elemento (configurações de rede)</span><span class="sxs-lookup"><span data-stu-id="f86dd-102">&lt;smtp&gt; Element (Network Settings)</span></span>
<span data-ttu-id="f86dd-103">Configura o formato de entrega, o método de entrega e de endereço para enviar emails.</span><span class="sxs-lookup"><span data-stu-id="f86dd-103">Configures the delivery format, delivery method, and from address for sending emails.</span></span>  
  
 <span data-ttu-id="f86dd-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="f86dd-104">\<configuration></span></span>  
<span data-ttu-id="f86dd-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="f86dd-105">\<system.net></span></span>  
<span data-ttu-id="f86dd-106">\<mailSettings></span><span class="sxs-lookup"><span data-stu-id="f86dd-106">\<mailSettings></span></span>  
<span data-ttu-id="f86dd-107">\<smtp></span><span class="sxs-lookup"><span data-stu-id="f86dd-107">\<smtp></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f86dd-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f86dd-108">Syntax</span></span>  
  
```xml  
      <smtp  
        deliveryFormat="format"   
        deliveryMethod="method"   
        from="from address">
          <specifiedPickupDirectory> … </ specifiedPickupDirectory >  
          <network> … </network>  
      </smtp>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f86dd-109">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="f86dd-109">Attributes and Elements</span></span>  
 <span data-ttu-id="f86dd-110">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="f86dd-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f86dd-111">Atributos</span><span class="sxs-lookup"><span data-stu-id="f86dd-111">Attributes</span></span>  
  
|<span data-ttu-id="f86dd-112">Atributo</span><span class="sxs-lookup"><span data-stu-id="f86dd-112">Attribute</span></span>|<span data-ttu-id="f86dd-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="f86dd-113">Description</span></span>|  
|---------------|-----------------|  
|`deliveryFormat`|<span data-ttu-id="f86dd-114">Especifica o formato de entrega de emails de saída.</span><span class="sxs-lookup"><span data-stu-id="f86dd-114">Specifies the delivery format for outgoing emails.</span></span> <span data-ttu-id="f86dd-115">Os valores aceitáveis são SevenBit e tratados internacionais.</span><span class="sxs-lookup"><span data-stu-id="f86dd-115">Acceptable values are SevenBit and International.</span></span>|  
|`deliveryMethod`|<span data-ttu-id="f86dd-116">Especifica o método de entrega de emails.</span><span class="sxs-lookup"><span data-stu-id="f86dd-116">Specifies the delivery method for emails.</span></span> <span data-ttu-id="f86dd-117">Os valores aceitáveis são specifiedPickupDirectory, pickupDirectoryFromIis e rede.</span><span class="sxs-lookup"><span data-stu-id="f86dd-117">Acceptable values are network, pickupDirectoryFromIis, and specifiedPickupDirectory.</span></span>|  
|`from`|<span data-ttu-id="f86dd-118">Especifica o endereço para emails de saída do.</span><span class="sxs-lookup"><span data-stu-id="f86dd-118">Specifies the from address for outgoing emails.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f86dd-119">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="f86dd-119">Child Elements</span></span>  
  
|<span data-ttu-id="f86dd-120">Atributo</span><span class="sxs-lookup"><span data-stu-id="f86dd-120">Attribute</span></span>|<span data-ttu-id="f86dd-121">Descrição</span><span class="sxs-lookup"><span data-stu-id="f86dd-121">Description</span></span>|  
|---------------|-----------------|  
|`specifiedPickupDirectory`|<span data-ttu-id="f86dd-122">Configura o diretório local para um servidor de transporte protocolo SMTP (Simple Mail).</span><span class="sxs-lookup"><span data-stu-id="f86dd-122">Configures the local directory for a Simple Mail Transport Protocol (SMTP) server.</span></span>|  
|`network`|<span data-ttu-id="f86dd-123">Configura as opções de rede para um servidor SMTP externo.</span><span class="sxs-lookup"><span data-stu-id="f86dd-123">Configures the network options for an external SMTP server.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="f86dd-124">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="f86dd-124">Parent Elements</span></span>  
  
|<span data-ttu-id="f86dd-125">**Elemento**</span><span class="sxs-lookup"><span data-stu-id="f86dd-125">**Element**</span></span>|<span data-ttu-id="f86dd-126">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="f86dd-126">**Description**</span></span>|  
|-----------------|---------------------|  
|<span data-ttu-id="f86dd-127">[\<mailSettings> Element (Network Settings)](../../../../../docs/framework/configure-apps/file-schema/network/mailsettings-element-network-settings.md) [Elemento mailSettings> (configurações de rede)]</span><span class="sxs-lookup"><span data-stu-id="f86dd-127">[\<mailSettings> Element (Network Settings)](../../../../../docs/framework/configure-apps/file-schema/network/mailsettings-element-network-settings.md)</span></span>|<span data-ttu-id="f86dd-128">Configura as opções de envio de email.</span><span class="sxs-lookup"><span data-stu-id="f86dd-128">Configures mail sending options.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="f86dd-129">Exemplo</span><span class="sxs-lookup"><span data-stu-id="f86dd-129">Example</span></span>  
 <span data-ttu-id="f86dd-130">O exemplo a seguir especifica os parâmetros apropriados de SMTP para enviar email usando as credenciais de rede padrão.</span><span class="sxs-lookup"><span data-stu-id="f86dd-130">The following example specifies the appropriate SMTP parameters to send email using the default network credentials.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <mailSettings>  
      <smtp deliveryMethod="network" deliveryFormat="SevenBit"  from="ben@contoso.com">  
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
  
## <a name="see-also"></a><span data-ttu-id="f86dd-131">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f86dd-131">See Also</span></span>  
 <xref:System.Net.Configuration.SmtpSection?displayProperty=nameWithType>  
 <xref:System.Net.Mail.SmtpClient?displayProperty=nameWithType>  
 <xref:System.Net.Mail.SmtpDeliveryFormat>  
 <xref:System.Net.Mail.SmtpDeliveryMethod>  
 [<span data-ttu-id="f86dd-132">Esquema de configurações de rede</span><span class="sxs-lookup"><span data-stu-id="f86dd-132">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
