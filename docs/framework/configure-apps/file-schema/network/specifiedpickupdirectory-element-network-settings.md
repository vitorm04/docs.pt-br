---
title: Elemento <specifiedPickupDirectory> (Configurações de Rede)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#specifiedPickupDirectory
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/mailSettings/smtp/specifiedPickupDirectory
helpviewer_keywords:
- specifiedPickupDirectory element
- <specifiedPickupDirectory> element
ms.assetid: 0121f49d-bff2-4bc6-af06-f1628dcd61f1
ms.openlocfilehash: 1acc724bb14c3610f14d06452c30b3d5dac42e13
ms.sourcegitcommit: 7f8eeef060ddeb2cabfa52843776faf652c5a1f5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/14/2019
ms.locfileid: "74089069"
---
# <a name="specifiedpickupdirectory-element-network-settings"></a><span data-ttu-id="5d15c-102">\<elemento de > specifiedPickupDirectory (configurações de rede)</span><span class="sxs-lookup"><span data-stu-id="5d15c-102">\<specifiedPickupDirectory> Element (Network Settings)</span></span>
<span data-ttu-id="5d15c-103">Configura o diretório local para um servidor SMTP (Simple Mail Transport Protocol).</span><span class="sxs-lookup"><span data-stu-id="5d15c-103">Configures the local directory for a Simple Mail Transport Protocol (SMTP) server.</span></span>  
  
<span data-ttu-id="5d15c-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="5d15c-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="5d15c-105">&nbsp;&nbsp;[ **\<System. net >** ](system-net-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="5d15c-105">&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)</span></span>\
<span data-ttu-id="5d15c-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<mailSettings >** ](mailsettings-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="5d15c-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<mailSettings>**](mailsettings-element-network-settings.md)</span></span>\
<span data-ttu-id="5d15c-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<smtp >** ](smtp-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="5d15c-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<smtp>**](smtp-element-network-settings.md)</span></span>\
<span data-ttu-id="5d15c-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<specifiedPickupDirectory >**</span><span class="sxs-lookup"><span data-stu-id="5d15c-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<specifiedPickupDirectory>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5d15c-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="5d15c-109">Syntax</span></span>  
  
```xml  
<specifiedPickupDirectory  
  pickupDirectoryLocation="directory"   
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5d15c-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="5d15c-110">Attributes and Elements</span></span>  
 <span data-ttu-id="5d15c-111">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="5d15c-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5d15c-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="5d15c-112">Attributes</span></span>  
  
|<span data-ttu-id="5d15c-113">Atributo</span><span class="sxs-lookup"><span data-stu-id="5d15c-113">Attribute</span></span>|<span data-ttu-id="5d15c-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="5d15c-114">Description</span></span>|  
|---------------|-----------------|  
|`pickupDirectoryLocation`|<span data-ttu-id="5d15c-115">O diretório em que os aplicativos salvam o email para processamento posterior pelo servidor SMTP.</span><span class="sxs-lookup"><span data-stu-id="5d15c-115">The directory where applications save email for later processing by the SMTP server.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5d15c-116">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="5d15c-116">Child Elements</span></span>  
 <span data-ttu-id="5d15c-117">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="5d15c-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="5d15c-118">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="5d15c-118">Parent Elements</span></span>  
  
|<span data-ttu-id="5d15c-119">Elemento</span><span class="sxs-lookup"><span data-stu-id="5d15c-119">Element</span></span>|<span data-ttu-id="5d15c-120">Descrição</span><span class="sxs-lookup"><span data-stu-id="5d15c-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5d15c-121">\<elemento > SMTP (configurações de rede)</span><span class="sxs-lookup"><span data-stu-id="5d15c-121">\<smtp> Element (Network Settings)</span></span>](smtp-element-network-settings.md)|<span data-ttu-id="5d15c-122">Configura as opções de envio de email do protocolo SMTP.</span><span class="sxs-lookup"><span data-stu-id="5d15c-122">Configures Simple Mail Transport Protocol (SMTP) mail sending options.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5d15c-123">Comentários</span><span class="sxs-lookup"><span data-stu-id="5d15c-123">Remarks</span></span>  
 <span data-ttu-id="5d15c-124">O atributo `specifiedPickupDirectory` define o diretório em que os aplicativos salvam mensagens de email a serem processadas pelo servidor SMTP.</span><span class="sxs-lookup"><span data-stu-id="5d15c-124">The `specifiedPickupDirectory` attribute sets the directory where applications save mail messages to be processed by the SMTP server.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5d15c-125">Exemplo</span><span class="sxs-lookup"><span data-stu-id="5d15c-125">Example</span></span>  
 <span data-ttu-id="5d15c-126">O exemplo a seguir especifica c:\maildrop como o diretório de recebimento de email.</span><span class="sxs-lookup"><span data-stu-id="5d15c-126">The following example specifies c:\maildrop as the mail pickup directory.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <mailSettings>  
      <smtp deliveryMethod="SpecifiedPickupDirectory">  
        <specifiedPickupDirectory  
          pickupDirectoryLocation="c:\maildrop"  
        />  
      </smtp>  
    </mailSettings>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="5d15c-127">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5d15c-127">See also</span></span>

- <xref:System.Net.Mail.SmtpClient?displayProperty=nameWithType>
- <xref:System.Net.Configuration.SmtpSection?displayProperty=nameWithType>
- <xref:System.Net.Configuration.SmtpSpecifiedPickupDirectoryElement?displayProperty=nameWithType>
- [<span data-ttu-id="5d15c-128">Esquema de configurações de rede</span><span class="sxs-lookup"><span data-stu-id="5d15c-128">Network Settings Schema</span></span>](index.md)
