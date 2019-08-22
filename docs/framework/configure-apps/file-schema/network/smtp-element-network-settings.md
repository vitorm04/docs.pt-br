---
title: Elemento <smtp> (Configurações de Rede)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/mailSettings/smtp
- http://schemas.microsoft.com/.NetConfiguration/v2.0#smtp
helpviewer_keywords:
- <smtp> element
- smtp element
ms.assetid: 220b0329-e384-4e0c-86b4-0945ad17efd9
ms.openlocfilehash: ac9405fdc6123a5a1352de06f94fefb6d7d4014b
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/21/2019
ms.locfileid: "69659116"
---
# <a name="smtp-element-network-settings"></a><span data-ttu-id="229d5-102">\<Elemento de > SMTP (configurações de rede)</span><span class="sxs-lookup"><span data-stu-id="229d5-102">\<smtp> Element (Network Settings)</span></span>
<span data-ttu-id="229d5-103">Configura o formato de entrega, o método de entrega e o endereço de remetente para enviar emails.</span><span class="sxs-lookup"><span data-stu-id="229d5-103">Configures the delivery format, delivery method, and from address for sending emails.</span></span>  
  
 <span data-ttu-id="229d5-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="229d5-104">\<configuration></span></span>  
<span data-ttu-id="229d5-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="229d5-105">\<system.net></span></span>  
<span data-ttu-id="229d5-106">\<mailSettings></span><span class="sxs-lookup"><span data-stu-id="229d5-106">\<mailSettings></span></span>  
<span data-ttu-id="229d5-107">\<smtp></span><span class="sxs-lookup"><span data-stu-id="229d5-107">\<smtp></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="229d5-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="229d5-108">Syntax</span></span>  
  
```xml  
<smtp  
  deliveryFormat="format"  
  deliveryMethod="method"  
  from="from address">
    <specifiedPickupDirectory>...</specifiedPickupDirectory>  
    <network>...</network>  
</smtp>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="229d5-109">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="229d5-109">Attributes and Elements</span></span>  
 <span data-ttu-id="229d5-110">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="229d5-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="229d5-111">Atributos</span><span class="sxs-lookup"><span data-stu-id="229d5-111">Attributes</span></span>  
  
|<span data-ttu-id="229d5-112">Atributo</span><span class="sxs-lookup"><span data-stu-id="229d5-112">Attribute</span></span>|<span data-ttu-id="229d5-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="229d5-113">Description</span></span>|  
|---------------|-----------------|  
|`deliveryFormat`|<span data-ttu-id="229d5-114">Especifica o formato de entrega para emails de saída.</span><span class="sxs-lookup"><span data-stu-id="229d5-114">Specifies the delivery format for outgoing emails.</span></span> <span data-ttu-id="229d5-115">Os valores aceitáveis são SevenBit e International.</span><span class="sxs-lookup"><span data-stu-id="229d5-115">Acceptable values are SevenBit and International.</span></span>|  
|`deliveryMethod`|<span data-ttu-id="229d5-116">Especifica o método de entrega para emails.</span><span class="sxs-lookup"><span data-stu-id="229d5-116">Specifies the delivery method for emails.</span></span> <span data-ttu-id="229d5-117">Os valores aceitáveis são Network, PickupDirectoryFromIis e SpecifiedPickupDirectory.</span><span class="sxs-lookup"><span data-stu-id="229d5-117">Acceptable values are Network, PickupDirectoryFromIis, and SpecifiedPickupDirectory.</span></span>|  
|`from`|<span data-ttu-id="229d5-118">Especifica o endereço de para emails de saída.</span><span class="sxs-lookup"><span data-stu-id="229d5-118">Specifies the from address for outgoing emails.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="229d5-119">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="229d5-119">Child Elements</span></span>  
  
|<span data-ttu-id="229d5-120">Atributo</span><span class="sxs-lookup"><span data-stu-id="229d5-120">Attribute</span></span>|<span data-ttu-id="229d5-121">Descrição</span><span class="sxs-lookup"><span data-stu-id="229d5-121">Description</span></span>|  
|---------------|-----------------|  
|`specifiedPickupDirectory`|<span data-ttu-id="229d5-122">Configura o diretório local para um servidor SMTP (Simple Mail Transport Protocol).</span><span class="sxs-lookup"><span data-stu-id="229d5-122">Configures the local directory for a Simple Mail Transport Protocol (SMTP) server.</span></span>|  
|`network`|<span data-ttu-id="229d5-123">Configura as opções de rede para um servidor SMTP externo.</span><span class="sxs-lookup"><span data-stu-id="229d5-123">Configures the network options for an external SMTP server.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="229d5-124">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="229d5-124">Parent Elements</span></span>  
  
|<span data-ttu-id="229d5-125">**Elemento**</span><span class="sxs-lookup"><span data-stu-id="229d5-125">**Element**</span></span>|<span data-ttu-id="229d5-126">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="229d5-126">**Description**</span></span>|  
|-----------------|---------------------|  
|<span data-ttu-id="229d5-127">[\<mailSettings> Element (Network Settings)](mailsettings-element-network-settings.md) [Elemento mailSettings> (configurações de rede)]</span><span class="sxs-lookup"><span data-stu-id="229d5-127">[\<mailSettings> Element (Network Settings)](mailsettings-element-network-settings.md)</span></span>|<span data-ttu-id="229d5-128">Configura as opções de envio de email.</span><span class="sxs-lookup"><span data-stu-id="229d5-128">Configures mail sending options.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="229d5-129">Exemplo</span><span class="sxs-lookup"><span data-stu-id="229d5-129">Example</span></span>  
 <span data-ttu-id="229d5-130">O exemplo a seguir especifica os parâmetros de SMTP apropriados para enviar email usando as credenciais de rede padrão.</span><span class="sxs-lookup"><span data-stu-id="229d5-130">The following example specifies the appropriate SMTP parameters to send email using the default network credentials.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="229d5-131">Consulte também</span><span class="sxs-lookup"><span data-stu-id="229d5-131">See also</span></span>

- <xref:System.Net.Configuration.SmtpSection?displayProperty=nameWithType>
- <xref:System.Net.Mail.SmtpClient?displayProperty=nameWithType>
- <xref:System.Net.Mail.SmtpDeliveryFormat>
- <xref:System.Net.Mail.SmtpDeliveryMethod>
- [<span data-ttu-id="229d5-132">Esquema de configurações de rede</span><span class="sxs-lookup"><span data-stu-id="229d5-132">Network Settings Schema</span></span>](index.md)
