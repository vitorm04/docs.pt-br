---
title: '&lt;SMTP&gt; (configurações de rede)'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/mailSettings/smtp
- http://schemas.microsoft.com/.NetConfiguration/v2.0#smtp
helpviewer_keywords:
- <smtp> element
- smtp element
ms.assetid: 220b0329-e384-4e0c-86b4-0945ad17efd9
ms.openlocfilehash: 362c5ba479c845a8183fe705e72ea3a12fb7a94c
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2018
ms.locfileid: "50195639"
---
# <a name="ltsmtpgt-element-network-settings"></a><span data-ttu-id="161bf-102">&lt;SMTP&gt; (configurações de rede)</span><span class="sxs-lookup"><span data-stu-id="161bf-102">&lt;smtp&gt; Element (Network Settings)</span></span>
<span data-ttu-id="161bf-103">Configura o formato de entrega, o método de entrega e o endereço para envio de emails.</span><span class="sxs-lookup"><span data-stu-id="161bf-103">Configures the delivery format, delivery method, and from address for sending emails.</span></span>  
  
 <span data-ttu-id="161bf-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="161bf-104">\<configuration></span></span>  
<span data-ttu-id="161bf-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="161bf-105">\<system.net></span></span>  
<span data-ttu-id="161bf-106">\<mailSettings></span><span class="sxs-lookup"><span data-stu-id="161bf-106">\<mailSettings></span></span>  
<span data-ttu-id="161bf-107">\<smtp></span><span class="sxs-lookup"><span data-stu-id="161bf-107">\<smtp></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="161bf-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="161bf-108">Syntax</span></span>  
  
```xml  
      <smtp  
        deliveryFormat="format"   
        deliveryMethod="method"   
        from="from address">
          <specifiedPickupDirectory> … </ specifiedPickupDirectory >  
          <network> … </network>  
      </smtp>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="161bf-109">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="161bf-109">Attributes and Elements</span></span>  
 <span data-ttu-id="161bf-110">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="161bf-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="161bf-111">Atributos</span><span class="sxs-lookup"><span data-stu-id="161bf-111">Attributes</span></span>  
  
|<span data-ttu-id="161bf-112">Atributo</span><span class="sxs-lookup"><span data-stu-id="161bf-112">Attribute</span></span>|<span data-ttu-id="161bf-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="161bf-113">Description</span></span>|  
|---------------|-----------------|  
|`deliveryFormat`|<span data-ttu-id="161bf-114">Especifica o formato de entrega para emails de saída.</span><span class="sxs-lookup"><span data-stu-id="161bf-114">Specifies the delivery format for outgoing emails.</span></span> <span data-ttu-id="161bf-115">Os valores aceitáveis são SevenBit e International.</span><span class="sxs-lookup"><span data-stu-id="161bf-115">Acceptable values are SevenBit and International.</span></span>|  
|`deliveryMethod`|<span data-ttu-id="161bf-116">Especifica o método de entrega para emails.</span><span class="sxs-lookup"><span data-stu-id="161bf-116">Specifies the delivery method for emails.</span></span> <span data-ttu-id="161bf-117">Os valores aceitáveis são rede, PickupDirectoryFromIis e SpecifiedPickupDirectory.</span><span class="sxs-lookup"><span data-stu-id="161bf-117">Acceptable values are Network, PickupDirectoryFromIis, and SpecifiedPickupDirectory.</span></span>|  
|`from`|<span data-ttu-id="161bf-118">Especifica o endereço para emails de saída.</span><span class="sxs-lookup"><span data-stu-id="161bf-118">Specifies the from address for outgoing emails.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="161bf-119">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="161bf-119">Child Elements</span></span>  
  
|<span data-ttu-id="161bf-120">Atributo</span><span class="sxs-lookup"><span data-stu-id="161bf-120">Attribute</span></span>|<span data-ttu-id="161bf-121">Descrição</span><span class="sxs-lookup"><span data-stu-id="161bf-121">Description</span></span>|  
|---------------|-----------------|  
|`specifiedPickupDirectory`|<span data-ttu-id="161bf-122">Configura o diretório local para um servidor de transporte protocolo SMTP (Simple Mail).</span><span class="sxs-lookup"><span data-stu-id="161bf-122">Configures the local directory for a Simple Mail Transport Protocol (SMTP) server.</span></span>|  
|`network`|<span data-ttu-id="161bf-123">Configura as opções de rede para um servidor SMTP externo.</span><span class="sxs-lookup"><span data-stu-id="161bf-123">Configures the network options for an external SMTP server.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="161bf-124">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="161bf-124">Parent Elements</span></span>  
  
|<span data-ttu-id="161bf-125">**Elemento**</span><span class="sxs-lookup"><span data-stu-id="161bf-125">**Element**</span></span>|<span data-ttu-id="161bf-126">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="161bf-126">**Description**</span></span>|  
|-----------------|---------------------|  
|<span data-ttu-id="161bf-127">[\<mailSettings> Element (Network Settings)](../../../../../docs/framework/configure-apps/file-schema/network/mailsettings-element-network-settings.md) [Elemento mailSettings> (configurações de rede)]</span><span class="sxs-lookup"><span data-stu-id="161bf-127">[\<mailSettings> Element (Network Settings)](../../../../../docs/framework/configure-apps/file-schema/network/mailsettings-element-network-settings.md)</span></span>|<span data-ttu-id="161bf-128">Configura as opções de envio de email.</span><span class="sxs-lookup"><span data-stu-id="161bf-128">Configures mail sending options.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="161bf-129">Exemplo</span><span class="sxs-lookup"><span data-stu-id="161bf-129">Example</span></span>  
 <span data-ttu-id="161bf-130">O exemplo a seguir especifica os parâmetros apropriados de SMTP para enviar email usando as credenciais de rede padrão.</span><span class="sxs-lookup"><span data-stu-id="161bf-130">The following example specifies the appropriate SMTP parameters to send email using the default network credentials.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <mailSettings>  
      <smtp deliveryMethod="Network" deliveryFormat="SevenBit"  from="ben@contoso.com">  
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
  
## <a name="see-also"></a><span data-ttu-id="161bf-131">Consulte também</span><span class="sxs-lookup"><span data-stu-id="161bf-131">See Also</span></span>  
- <xref:System.Net.Configuration.SmtpSection?displayProperty=nameWithType>  
- <xref:System.Net.Mail.SmtpClient?displayProperty=nameWithType>  
- <xref:System.Net.Mail.SmtpDeliveryFormat>  
- <xref:System.Net.Mail.SmtpDeliveryMethod>  
- [<span data-ttu-id="161bf-132">Esquema de configurações de rede</span><span class="sxs-lookup"><span data-stu-id="161bf-132">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
