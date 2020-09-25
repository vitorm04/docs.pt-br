---
title: Elemento <specifiedPickupDirectory> (Configurações de Rede)
description: O <specifiedPickupDirectory> elemento de configurações de rede configura o diretório local para uma opção de servidor SMTP no .NET Framework.
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#specifiedPickupDirectory
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/mailSettings/smtp/specifiedPickupDirectory
helpviewer_keywords:
- specifiedPickupDirectory element
- <specifiedPickupDirectory> element
ms.assetid: 0121f49d-bff2-4bc6-af06-f1628dcd61f1
ms.openlocfilehash: 5bb7fc5405b1ee2f0f054bc6e9f043a3f9fcd1ec
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91176156"
---
# <a name="specifiedpickupdirectory-element-network-settings"></a><span data-ttu-id="f13ac-103">Elemento \<specifiedPickupDirectory> (Configurações de Rede)</span><span class="sxs-lookup"><span data-stu-id="f13ac-103">\<specifiedPickupDirectory> Element (Network Settings)</span></span>

<span data-ttu-id="f13ac-104">Configura o diretório local para um servidor SMTP (Simple Mail Transport Protocol).</span><span class="sxs-lookup"><span data-stu-id="f13ac-104">Configures the local directory for a Simple Mail Transport Protocol (SMTP) server.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<mailSettings>**](mailsettings-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<smtp>**](smtp-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<specifiedPickupDirectory>**  
  
## <a name="syntax"></a><span data-ttu-id="f13ac-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f13ac-105">Syntax</span></span>  
  
```xml  
<specifiedPickupDirectory  
  pickupDirectoryLocation="directory"
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f13ac-106">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="f13ac-106">Attributes and Elements</span></span>  

 <span data-ttu-id="f13ac-107">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="f13ac-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f13ac-108">Atributos</span><span class="sxs-lookup"><span data-stu-id="f13ac-108">Attributes</span></span>  
  
|<span data-ttu-id="f13ac-109">Atributo</span><span class="sxs-lookup"><span data-stu-id="f13ac-109">Attribute</span></span>|<span data-ttu-id="f13ac-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="f13ac-110">Description</span></span>|  
|---------------|-----------------|  
|`pickupDirectoryLocation`|<span data-ttu-id="f13ac-111">O diretório em que os aplicativos salvam o email para processamento posterior pelo servidor SMTP.</span><span class="sxs-lookup"><span data-stu-id="f13ac-111">The directory where applications save email for later processing by the SMTP server.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f13ac-112">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="f13ac-112">Child Elements</span></span>  

 <span data-ttu-id="f13ac-113">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="f13ac-113">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="f13ac-114">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="f13ac-114">Parent Elements</span></span>  
  
|<span data-ttu-id="f13ac-115">Elemento</span><span class="sxs-lookup"><span data-stu-id="f13ac-115">Element</span></span>|<span data-ttu-id="f13ac-116">Descrição</span><span class="sxs-lookup"><span data-stu-id="f13ac-116">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f13ac-117">\<smtp> Elemento (configurações de rede)</span><span class="sxs-lookup"><span data-stu-id="f13ac-117">\<smtp> Element (Network Settings)</span></span>](smtp-element-network-settings.md)|<span data-ttu-id="f13ac-118">Configura as opções de envio de email do protocolo SMTP.</span><span class="sxs-lookup"><span data-stu-id="f13ac-118">Configures Simple Mail Transport Protocol (SMTP) mail sending options.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f13ac-119">Comentários</span><span class="sxs-lookup"><span data-stu-id="f13ac-119">Remarks</span></span>  

 <span data-ttu-id="f13ac-120">O `specifiedPickupDirectory` atributo define o diretório em que os aplicativos salvam mensagens de email a serem processadas pelo servidor SMTP.</span><span class="sxs-lookup"><span data-stu-id="f13ac-120">The `specifiedPickupDirectory` attribute sets the directory where applications save mail messages to be processed by the SMTP server.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f13ac-121">Exemplo</span><span class="sxs-lookup"><span data-stu-id="f13ac-121">Example</span></span>  

 <span data-ttu-id="f13ac-122">O exemplo a seguir especifica c:\maildrop como o diretório de recebimento de email.</span><span class="sxs-lookup"><span data-stu-id="f13ac-122">The following example specifies c:\maildrop as the mail pickup directory.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="f13ac-123">Veja também</span><span class="sxs-lookup"><span data-stu-id="f13ac-123">See also</span></span>

- <xref:System.Net.Mail.SmtpClient?displayProperty=nameWithType>
- <xref:System.Net.Configuration.SmtpSection?displayProperty=nameWithType>
- <xref:System.Net.Configuration.SmtpSpecifiedPickupDirectoryElement?displayProperty=nameWithType>
- [<span data-ttu-id="f13ac-124">Esquema de configurações de rede</span><span class="sxs-lookup"><span data-stu-id="f13ac-124">Network Settings Schema</span></span>](index.md)
