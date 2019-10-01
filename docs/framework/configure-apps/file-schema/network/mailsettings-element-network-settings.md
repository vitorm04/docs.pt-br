---
title: Elemento <mailSettings> (Configurações de Rede)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#mailSettings
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/mailSettings
helpviewer_keywords:
- mailSettings element
- <mailSettings> element
ms.assetid: 54f0f153-17e5-4f49-afdc-deadb940c9c1
ms.openlocfilehash: fb4c8844ed3eb13af483c214d659090c0c563c33
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/01/2019
ms.locfileid: "71698072"
---
# <a name="mailsettings-element-network-settings"></a><span data-ttu-id="08c56-102">\<mailSettings > elemento (configurações de rede)</span><span class="sxs-lookup"><span data-stu-id="08c56-102">\<mailSettings> Element (Network Settings)</span></span>
<span data-ttu-id="08c56-103">Configura as opções de envio de email.</span><span class="sxs-lookup"><span data-stu-id="08c56-103">Configures mail sending options.</span></span>  

[<span data-ttu-id="08c56-104"> **\<configuration>** </span><span class="sxs-lookup"><span data-stu-id="08c56-104">**\<configuration>**</span></span>](../configuration-element.md)  
<span data-ttu-id="08c56-105">&nbsp; @ no__t-1[ **@no__t -4System. net >** ](system-net-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="08c56-105">&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)</span></span>  
<span data-ttu-id="08c56-106">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 **\<mailSettings >**</span><span class="sxs-lookup"><span data-stu-id="08c56-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<mailSettings>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="08c56-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="08c56-107">Syntax</span></span>  
  
```xml  
<mailSettings>
  <smtp>...</smtp>  
</mailSettings>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="08c56-108">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="08c56-108">Attributes and Elements</span></span>  
 <span data-ttu-id="08c56-109">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="08c56-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="08c56-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="08c56-110">Attributes</span></span>  
 <span data-ttu-id="08c56-111">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="08c56-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="08c56-112">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="08c56-112">Child Elements</span></span>  
  
|<span data-ttu-id="08c56-113">Atributo</span><span class="sxs-lookup"><span data-stu-id="08c56-113">Attribute</span></span>|<span data-ttu-id="08c56-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="08c56-114">Description</span></span>|  
|---------------|-----------------|  
|[<span data-ttu-id="08c56-115">\<smtp > elemento (configurações de rede)</span><span class="sxs-lookup"><span data-stu-id="08c56-115">\<smtp> Element (Network Settings)</span></span>](smtp-element-network-settings.md)|<span data-ttu-id="08c56-116">Configura opções de protocolo de transporte de email simples.</span><span class="sxs-lookup"><span data-stu-id="08c56-116">Configures Simple Mail Transport Protocol options.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="08c56-117">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="08c56-117">Parent Elements</span></span>  
  
|<span data-ttu-id="08c56-118">**Elemento**</span><span class="sxs-lookup"><span data-stu-id="08c56-118">**Element**</span></span>|<span data-ttu-id="08c56-119">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="08c56-119">**Description**</span></span>|  
|-----------------|---------------------|  
|<span data-ttu-id="08c56-120">Elemento [\<system.Net> (configurações de rede)](system-net-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="08c56-120">[\<system.Net> Element (Network Settings)](system-net-element-network-settings.md)</span></span>|<span data-ttu-id="08c56-121">Contém configurações que especificam como o .NET Framework se conecta à rede.</span><span class="sxs-lookup"><span data-stu-id="08c56-121">Contains settings that specify how the .NET Framework connects to the network.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="08c56-122">Exemplo</span><span class="sxs-lookup"><span data-stu-id="08c56-122">Example</span></span>  
 <span data-ttu-id="08c56-123">O exemplo a seguir especifica os parâmetros de SMTP apropriados para enviar email usando as credenciais de rede padrão.</span><span class="sxs-lookup"><span data-stu-id="08c56-123">The following example specifies the appropriate SMTP parameters to send email using the default network credentials.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <mailSettings>  
      <smtp deliveryMethod="Network">  
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
  
## <a name="see-also"></a><span data-ttu-id="08c56-124">Consulte também</span><span class="sxs-lookup"><span data-stu-id="08c56-124">See also</span></span>

- <xref:System.Net.Mail.SmtpClient>
- [<span data-ttu-id="08c56-125">Esquema de configurações de rede</span><span class="sxs-lookup"><span data-stu-id="08c56-125">Network Settings Schema</span></span>](index.md)
