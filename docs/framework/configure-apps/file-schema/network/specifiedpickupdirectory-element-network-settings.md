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
ms.openlocfilehash: 4b0cbaf9a7bfe2a9b1610811f4201253d219a6b2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79154602"
---
# <a name="specifiedpickupdirectory-element-network-settings"></a><span data-ttu-id="60bba-102">\<elemento> de> pickup (configurações de rede) especificado</span><span class="sxs-lookup"><span data-stu-id="60bba-102">\<specifiedPickupDirectory> Element (Network Settings)</span></span>
<span data-ttu-id="60bba-103">Configura o diretório local para um servidor SMTP (Simple Mail Transport Protocol, protocolo de transporte de correio simples).</span><span class="sxs-lookup"><span data-stu-id="60bba-103">Configures the local directory for a Simple Mail Transport Protocol (SMTP) server.</span></span>  
  
<span data-ttu-id="60bba-104">[**\<>de configuração**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="60bba-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="60bba-105">&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="60bba-105">&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)</span></span>\
<span data-ttu-id="60bba-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<>de configurações de e-mail**](mailsettings-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="60bba-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<mailSettings>**](mailsettings-element-network-settings.md)</span></span>\
<span data-ttu-id="60bba-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<smtp>**](smtp-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="60bba-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<smtp>**](smtp-element-network-settings.md)</span></span>\
<span data-ttu-id="60bba-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<especificadoPickupDiretório>**</span><span class="sxs-lookup"><span data-stu-id="60bba-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<specifiedPickupDirectory>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="60bba-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="60bba-109">Syntax</span></span>  
  
```xml  
<specifiedPickupDirectory  
  pickupDirectoryLocation="directory"
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="60bba-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="60bba-110">Attributes and Elements</span></span>  
 <span data-ttu-id="60bba-111">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="60bba-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="60bba-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="60bba-112">Attributes</span></span>  
  
|<span data-ttu-id="60bba-113">Atributo</span><span class="sxs-lookup"><span data-stu-id="60bba-113">Attribute</span></span>|<span data-ttu-id="60bba-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="60bba-114">Description</span></span>|  
|---------------|-----------------|  
|`pickupDirectoryLocation`|<span data-ttu-id="60bba-115">O diretório onde os aplicativos salvam o e-mail para posterior processamento pelo servidor SMTP.</span><span class="sxs-lookup"><span data-stu-id="60bba-115">The directory where applications save email for later processing by the SMTP server.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="60bba-116">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="60bba-116">Child Elements</span></span>  
 <span data-ttu-id="60bba-117">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="60bba-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="60bba-118">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="60bba-118">Parent Elements</span></span>  
  
|<span data-ttu-id="60bba-119">Elemento</span><span class="sxs-lookup"><span data-stu-id="60bba-119">Element</span></span>|<span data-ttu-id="60bba-120">Descrição</span><span class="sxs-lookup"><span data-stu-id="60bba-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="60bba-121">\<smtp elemento> (configurações de rede)</span><span class="sxs-lookup"><span data-stu-id="60bba-121">\<smtp> Element (Network Settings)</span></span>](smtp-element-network-settings.md)|<span data-ttu-id="60bba-122">Configura opções de envio de e-mails do Simple Mail Transport Protocol (SMTP).</span><span class="sxs-lookup"><span data-stu-id="60bba-122">Configures Simple Mail Transport Protocol (SMTP) mail sending options.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="60bba-123">Comentários</span><span class="sxs-lookup"><span data-stu-id="60bba-123">Remarks</span></span>  
 <span data-ttu-id="60bba-124">O `specifiedPickupDirectory` atributo define o diretório onde os aplicativos salvam mensagens de e-mail para serem processadas pelo servidor SMTP.</span><span class="sxs-lookup"><span data-stu-id="60bba-124">The `specifiedPickupDirectory` attribute sets the directory where applications save mail messages to be processed by the SMTP server.</span></span>  
  
## <a name="example"></a><span data-ttu-id="60bba-125">Exemplo</span><span class="sxs-lookup"><span data-stu-id="60bba-125">Example</span></span>  
 <span data-ttu-id="60bba-126">O exemplo a seguir especifica c:\emaildrop como o diretório de captação de e-mails.</span><span class="sxs-lookup"><span data-stu-id="60bba-126">The following example specifies c:\maildrop as the mail pickup directory.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="60bba-127">Confira também</span><span class="sxs-lookup"><span data-stu-id="60bba-127">See also</span></span>

- <xref:System.Net.Mail.SmtpClient?displayProperty=nameWithType>
- <xref:System.Net.Configuration.SmtpSection?displayProperty=nameWithType>
- <xref:System.Net.Configuration.SmtpSpecifiedPickupDirectoryElement?displayProperty=nameWithType>
- [<span data-ttu-id="60bba-128">Esquema de configurações de rede</span><span class="sxs-lookup"><span data-stu-id="60bba-128">Network Settings Schema</span></span>](index.md)
