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
ms.openlocfilehash: 58f496b4a07f7d5531df897dd54bb6176111f1c4
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91178314"
---
# <a name="smtp-element-network-settings"></a><span data-ttu-id="58d18-103">Elemento \<smtp> (Configurações de Rede)</span><span class="sxs-lookup"><span data-stu-id="58d18-103">\<smtp> Element (Network Settings)</span></span>

<span data-ttu-id="58d18-104">Configura o formato de entrega, o método de entrega e o endereço de remetente para enviar emails.</span><span class="sxs-lookup"><span data-stu-id="58d18-104">Configures the delivery format, delivery method, and from address for sending emails.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<mailSettings>**](mailsettings-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<smtp>**
  
## <a name="syntax"></a><span data-ttu-id="58d18-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="58d18-105">Syntax</span></span>  
  
```xml  
<smtp  
  deliveryFormat="format"  
  deliveryMethod="method"  
  from="from address">
    <specifiedPickupDirectory>...</specifiedPickupDirectory>  
    <network>...</network>  
</smtp>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="58d18-106">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="58d18-106">Attributes and Elements</span></span>  

 <span data-ttu-id="58d18-107">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="58d18-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="58d18-108">Atributos</span><span class="sxs-lookup"><span data-stu-id="58d18-108">Attributes</span></span>  
  
|<span data-ttu-id="58d18-109">Atributo</span><span class="sxs-lookup"><span data-stu-id="58d18-109">Attribute</span></span>|<span data-ttu-id="58d18-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="58d18-110">Description</span></span>|  
|---------------|-----------------|  
|`deliveryFormat`|<span data-ttu-id="58d18-111">Especifica o formato de entrega para emails de saída.</span><span class="sxs-lookup"><span data-stu-id="58d18-111">Specifies the delivery format for outgoing emails.</span></span> <span data-ttu-id="58d18-112">Os valores aceitáveis são SevenBit e International.</span><span class="sxs-lookup"><span data-stu-id="58d18-112">Acceptable values are SevenBit and International.</span></span>|  
|`deliveryMethod`|<span data-ttu-id="58d18-113">Especifica o método de entrega para emails.</span><span class="sxs-lookup"><span data-stu-id="58d18-113">Specifies the delivery method for emails.</span></span> <span data-ttu-id="58d18-114">Os valores aceitáveis são Network, PickupDirectoryFromIis e SpecifiedPickupDirectory.</span><span class="sxs-lookup"><span data-stu-id="58d18-114">Acceptable values are Network, PickupDirectoryFromIis, and SpecifiedPickupDirectory.</span></span>|  
|`from`|<span data-ttu-id="58d18-115">Especifica o endereço de para emails de saída.</span><span class="sxs-lookup"><span data-stu-id="58d18-115">Specifies the from address for outgoing emails.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="58d18-116">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="58d18-116">Child Elements</span></span>  
  
|<span data-ttu-id="58d18-117">Atributo</span><span class="sxs-lookup"><span data-stu-id="58d18-117">Attribute</span></span>|<span data-ttu-id="58d18-118">Descrição</span><span class="sxs-lookup"><span data-stu-id="58d18-118">Description</span></span>|  
|---------------|-----------------|  
|`specifiedPickupDirectory`|<span data-ttu-id="58d18-119">Configura o diretório local para um servidor SMTP (Simple Mail Transport Protocol).</span><span class="sxs-lookup"><span data-stu-id="58d18-119">Configures the local directory for a Simple Mail Transport Protocol (SMTP) server.</span></span>|  
|`network`|<span data-ttu-id="58d18-120">Configura as opções de rede para um servidor SMTP externo.</span><span class="sxs-lookup"><span data-stu-id="58d18-120">Configures the network options for an external SMTP server.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="58d18-121">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="58d18-121">Parent Elements</span></span>  
  
|<span data-ttu-id="58d18-122">**Element**</span><span class="sxs-lookup"><span data-stu-id="58d18-122">**Element**</span></span>|<span data-ttu-id="58d18-123">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="58d18-123">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="58d18-124">\<mailSettings> Elemento (configurações de rede)</span><span class="sxs-lookup"><span data-stu-id="58d18-124">\<mailSettings> Element (Network Settings)</span></span>](mailsettings-element-network-settings.md)|<span data-ttu-id="58d18-125">Configura as opções de envio de email.</span><span class="sxs-lookup"><span data-stu-id="58d18-125">Configures mail sending options.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="58d18-126">Exemplo</span><span class="sxs-lookup"><span data-stu-id="58d18-126">Example</span></span>  

 <span data-ttu-id="58d18-127">O exemplo a seguir especifica os parâmetros de SMTP apropriados para enviar email usando as credenciais de rede padrão.</span><span class="sxs-lookup"><span data-stu-id="58d18-127">The following example specifies the appropriate SMTP parameters to send email using the default network credentials.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="58d18-128">Veja também</span><span class="sxs-lookup"><span data-stu-id="58d18-128">See also</span></span>

- <xref:System.Net.Configuration.SmtpSection?displayProperty=nameWithType>
- <xref:System.Net.Mail.SmtpClient?displayProperty=nameWithType>
- <xref:System.Net.Mail.SmtpDeliveryFormat>
- <xref:System.Net.Mail.SmtpDeliveryMethod>
- [<span data-ttu-id="58d18-129">Esquema de configurações de rede</span><span class="sxs-lookup"><span data-stu-id="58d18-129">Network Settings Schema</span></span>](index.md)
