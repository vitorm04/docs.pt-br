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
ms.openlocfilehash: 625c3cb82a8659c742b540724e5cf31be65a705e
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/06/2020
ms.locfileid: "74089095"
---
# <a name="smtp-element-network-settings"></a><span data-ttu-id="3ef1c-102">Elemento \<smtp> (Configurações de Rede)</span><span class="sxs-lookup"><span data-stu-id="3ef1c-102">\<smtp> Element (Network Settings)</span></span>
<span data-ttu-id="3ef1c-103">Configura o formato de entrega, o método de entrega e o endereço de remetente para enviar emails.</span><span class="sxs-lookup"><span data-stu-id="3ef1c-103">Configures the delivery format, delivery method, and from address for sending emails.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<mailSettings>**](mailsettings-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<smtp>**
  
## <a name="syntax"></a><span data-ttu-id="3ef1c-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="3ef1c-104">Syntax</span></span>  
  
```xml  
<smtp  
  deliveryFormat="format"  
  deliveryMethod="method"  
  from="from address">
    <specifiedPickupDirectory>...</specifiedPickupDirectory>  
    <network>...</network>  
</smtp>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3ef1c-105">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="3ef1c-105">Attributes and Elements</span></span>  
 <span data-ttu-id="3ef1c-106">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="3ef1c-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3ef1c-107">Atributos</span><span class="sxs-lookup"><span data-stu-id="3ef1c-107">Attributes</span></span>  
  
|<span data-ttu-id="3ef1c-108">Atributo</span><span class="sxs-lookup"><span data-stu-id="3ef1c-108">Attribute</span></span>|<span data-ttu-id="3ef1c-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="3ef1c-109">Description</span></span>|  
|---------------|-----------------|  
|`deliveryFormat`|<span data-ttu-id="3ef1c-110">Especifica o formato de entrega para emails de saída.</span><span class="sxs-lookup"><span data-stu-id="3ef1c-110">Specifies the delivery format for outgoing emails.</span></span> <span data-ttu-id="3ef1c-111">Os valores aceitáveis são SevenBit e International.</span><span class="sxs-lookup"><span data-stu-id="3ef1c-111">Acceptable values are SevenBit and International.</span></span>|  
|`deliveryMethod`|<span data-ttu-id="3ef1c-112">Especifica o método de entrega para emails.</span><span class="sxs-lookup"><span data-stu-id="3ef1c-112">Specifies the delivery method for emails.</span></span> <span data-ttu-id="3ef1c-113">Os valores aceitáveis são Network, PickupDirectoryFromIis e SpecifiedPickupDirectory.</span><span class="sxs-lookup"><span data-stu-id="3ef1c-113">Acceptable values are Network, PickupDirectoryFromIis, and SpecifiedPickupDirectory.</span></span>|  
|`from`|<span data-ttu-id="3ef1c-114">Especifica o endereço de para emails de saída.</span><span class="sxs-lookup"><span data-stu-id="3ef1c-114">Specifies the from address for outgoing emails.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="3ef1c-115">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="3ef1c-115">Child Elements</span></span>  
  
|<span data-ttu-id="3ef1c-116">Atributo</span><span class="sxs-lookup"><span data-stu-id="3ef1c-116">Attribute</span></span>|<span data-ttu-id="3ef1c-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="3ef1c-117">Description</span></span>|  
|---------------|-----------------|  
|`specifiedPickupDirectory`|<span data-ttu-id="3ef1c-118">Configura o diretório local para um servidor SMTP (Simple Mail Transport Protocol).</span><span class="sxs-lookup"><span data-stu-id="3ef1c-118">Configures the local directory for a Simple Mail Transport Protocol (SMTP) server.</span></span>|  
|`network`|<span data-ttu-id="3ef1c-119">Configura as opções de rede para um servidor SMTP externo.</span><span class="sxs-lookup"><span data-stu-id="3ef1c-119">Configures the network options for an external SMTP server.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="3ef1c-120">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="3ef1c-120">Parent Elements</span></span>  
  
|<span data-ttu-id="3ef1c-121">**Elemento**</span><span class="sxs-lookup"><span data-stu-id="3ef1c-121">**Element**</span></span>|<span data-ttu-id="3ef1c-122">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="3ef1c-122">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="3ef1c-123">\<mailSettings>Elemento (configurações de rede)</span><span class="sxs-lookup"><span data-stu-id="3ef1c-123">\<mailSettings> Element (Network Settings)</span></span>](mailsettings-element-network-settings.md)|<span data-ttu-id="3ef1c-124">Configura as opções de envio de email.</span><span class="sxs-lookup"><span data-stu-id="3ef1c-124">Configures mail sending options.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="3ef1c-125">Exemplo</span><span class="sxs-lookup"><span data-stu-id="3ef1c-125">Example</span></span>  
 <span data-ttu-id="3ef1c-126">O exemplo a seguir especifica os parâmetros de SMTP apropriados para enviar email usando as credenciais de rede padrão.</span><span class="sxs-lookup"><span data-stu-id="3ef1c-126">The following example specifies the appropriate SMTP parameters to send email using the default network credentials.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="3ef1c-127">Confira também</span><span class="sxs-lookup"><span data-stu-id="3ef1c-127">See also</span></span>

- <xref:System.Net.Configuration.SmtpSection?displayProperty=nameWithType>
- <xref:System.Net.Mail.SmtpClient?displayProperty=nameWithType>
- <xref:System.Net.Mail.SmtpDeliveryFormat>
- <xref:System.Net.Mail.SmtpDeliveryMethod>
- [<span data-ttu-id="3ef1c-128">Esquema de configurações de rede</span><span class="sxs-lookup"><span data-stu-id="3ef1c-128">Network Settings Schema</span></span>](index.md)
