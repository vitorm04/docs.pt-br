---
title: Elemento <smtp> (Configurações de Rede)
description: O <smtp> elemento de configurações de rede configura o formato de entrega, o método de entrega e o endereço de remetente para as opções de envio de emails no .NET Framework.
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/mailSettings/smtp
- http://schemas.microsoft.com/.NetConfiguration/v2.0#smtp
helpviewer_keywords:
- <smtp> element
- smtp element
ms.assetid: 220b0329-e384-4e0c-86b4-0945ad17efd9
ms.openlocfilehash: b30b82922a69ea660f4c4abfd808e89fa9945183
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84504505"
---
# <a name="smtp-element-network-settings"></a><span data-ttu-id="926a9-103">Elemento \<smtp> (Configurações de Rede)</span><span class="sxs-lookup"><span data-stu-id="926a9-103">\<smtp> Element (Network Settings)</span></span>
<span data-ttu-id="926a9-104">Configura o formato de entrega, o método de entrega e o endereço de remetente para enviar emails.</span><span class="sxs-lookup"><span data-stu-id="926a9-104">Configures the delivery format, delivery method, and from address for sending emails.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<mailSettings>**](mailsettings-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<smtp>**
  
## <a name="syntax"></a><span data-ttu-id="926a9-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="926a9-105">Syntax</span></span>  
  
```xml  
<smtp  
  deliveryFormat="format"  
  deliveryMethod="method"  
  from="from address">
    <specifiedPickupDirectory>...</specifiedPickupDirectory>  
    <network>...</network>  
</smtp>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="926a9-106">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="926a9-106">Attributes and Elements</span></span>  
 <span data-ttu-id="926a9-107">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="926a9-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="926a9-108">Atributos</span><span class="sxs-lookup"><span data-stu-id="926a9-108">Attributes</span></span>  
  
|<span data-ttu-id="926a9-109">Atributo</span><span class="sxs-lookup"><span data-stu-id="926a9-109">Attribute</span></span>|<span data-ttu-id="926a9-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="926a9-110">Description</span></span>|  
|---------------|-----------------|  
|`deliveryFormat`|<span data-ttu-id="926a9-111">Especifica o formato de entrega para emails de saída.</span><span class="sxs-lookup"><span data-stu-id="926a9-111">Specifies the delivery format for outgoing emails.</span></span> <span data-ttu-id="926a9-112">Os valores aceitáveis são SevenBit e International.</span><span class="sxs-lookup"><span data-stu-id="926a9-112">Acceptable values are SevenBit and International.</span></span>|  
|`deliveryMethod`|<span data-ttu-id="926a9-113">Especifica o método de entrega para emails.</span><span class="sxs-lookup"><span data-stu-id="926a9-113">Specifies the delivery method for emails.</span></span> <span data-ttu-id="926a9-114">Os valores aceitáveis são Network, PickupDirectoryFromIis e SpecifiedPickupDirectory.</span><span class="sxs-lookup"><span data-stu-id="926a9-114">Acceptable values are Network, PickupDirectoryFromIis, and SpecifiedPickupDirectory.</span></span>|  
|`from`|<span data-ttu-id="926a9-115">Especifica o endereço de para emails de saída.</span><span class="sxs-lookup"><span data-stu-id="926a9-115">Specifies the from address for outgoing emails.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="926a9-116">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="926a9-116">Child Elements</span></span>  
  
|<span data-ttu-id="926a9-117">Atributo</span><span class="sxs-lookup"><span data-stu-id="926a9-117">Attribute</span></span>|<span data-ttu-id="926a9-118">Descrição</span><span class="sxs-lookup"><span data-stu-id="926a9-118">Description</span></span>|  
|---------------|-----------------|  
|`specifiedPickupDirectory`|<span data-ttu-id="926a9-119">Configura o diretório local para um servidor SMTP (Simple Mail Transport Protocol).</span><span class="sxs-lookup"><span data-stu-id="926a9-119">Configures the local directory for a Simple Mail Transport Protocol (SMTP) server.</span></span>|  
|`network`|<span data-ttu-id="926a9-120">Configura as opções de rede para um servidor SMTP externo.</span><span class="sxs-lookup"><span data-stu-id="926a9-120">Configures the network options for an external SMTP server.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="926a9-121">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="926a9-121">Parent Elements</span></span>  
  
|<span data-ttu-id="926a9-122">**Elemento**</span><span class="sxs-lookup"><span data-stu-id="926a9-122">**Element**</span></span>|<span data-ttu-id="926a9-123">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="926a9-123">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="926a9-124">\<mailSettings>Elemento (configurações de rede)</span><span class="sxs-lookup"><span data-stu-id="926a9-124">\<mailSettings> Element (Network Settings)</span></span>](mailsettings-element-network-settings.md)|<span data-ttu-id="926a9-125">Configura as opções de envio de email.</span><span class="sxs-lookup"><span data-stu-id="926a9-125">Configures mail sending options.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="926a9-126">Exemplo</span><span class="sxs-lookup"><span data-stu-id="926a9-126">Example</span></span>  
 <span data-ttu-id="926a9-127">O exemplo a seguir especifica os parâmetros de SMTP apropriados para enviar email usando as credenciais de rede padrão.</span><span class="sxs-lookup"><span data-stu-id="926a9-127">The following example specifies the appropriate SMTP parameters to send email using the default network credentials.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="926a9-128">Confira também</span><span class="sxs-lookup"><span data-stu-id="926a9-128">See also</span></span>

- <xref:System.Net.Configuration.SmtpSection?displayProperty=nameWithType>
- <xref:System.Net.Mail.SmtpClient?displayProperty=nameWithType>
- <xref:System.Net.Mail.SmtpDeliveryFormat>
- <xref:System.Net.Mail.SmtpDeliveryMethod>
- [<span data-ttu-id="926a9-129">Esquema de configurações de rede</span><span class="sxs-lookup"><span data-stu-id="926a9-129">Network Settings Schema</span></span>](index.md)
