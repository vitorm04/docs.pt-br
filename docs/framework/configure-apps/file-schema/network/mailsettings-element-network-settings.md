---
title: Elemento <mailSettings> (Configurações de Rede)
description: O <mailSettings> elemento de configurações de rede configura as opções de envio de email no .NET Framework.
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#mailSettings
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/mailSettings
helpviewer_keywords:
- mailSettings element
- <mailSettings> element
ms.assetid: 54f0f153-17e5-4f49-afdc-deadb940c9c1
ms.openlocfilehash: a146874acc21f52507b37b1751c648792e23c8bb
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91158845"
---
# <a name="mailsettings-element-network-settings"></a><span data-ttu-id="207ba-103">Elemento \<mailSettings> (Configurações de Rede)</span><span class="sxs-lookup"><span data-stu-id="207ba-103">\<mailSettings> Element (Network Settings)</span></span>

<span data-ttu-id="207ba-104">Configura as opções de envio de email.</span><span class="sxs-lookup"><span data-stu-id="207ba-104">Configures mail sending options.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<mailSettings>**

## <a name="syntax"></a><span data-ttu-id="207ba-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="207ba-105">Syntax</span></span>  
  
```xml  
<mailSettings>
  <smtp>...</smtp>  
</mailSettings>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="207ba-106">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="207ba-106">Attributes and Elements</span></span>  

 <span data-ttu-id="207ba-107">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="207ba-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="207ba-108">Atributos</span><span class="sxs-lookup"><span data-stu-id="207ba-108">Attributes</span></span>  

 <span data-ttu-id="207ba-109">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="207ba-109">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="207ba-110">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="207ba-110">Child Elements</span></span>  
  
|<span data-ttu-id="207ba-111">Atributo</span><span class="sxs-lookup"><span data-stu-id="207ba-111">Attribute</span></span>|<span data-ttu-id="207ba-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="207ba-112">Description</span></span>|  
|---------------|-----------------|  
|[<span data-ttu-id="207ba-113">\<smtp> Elemento (configurações de rede)</span><span class="sxs-lookup"><span data-stu-id="207ba-113">\<smtp> Element (Network Settings)</span></span>](smtp-element-network-settings.md)|<span data-ttu-id="207ba-114">Configura opções de protocolo de transporte de email simples.</span><span class="sxs-lookup"><span data-stu-id="207ba-114">Configures Simple Mail Transport Protocol options.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="207ba-115">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="207ba-115">Parent Elements</span></span>  
  
|<span data-ttu-id="207ba-116">**Element**</span><span class="sxs-lookup"><span data-stu-id="207ba-116">**Element**</span></span>|<span data-ttu-id="207ba-117">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="207ba-117">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="207ba-118">\<system.Net> Elemento (configurações de rede)</span><span class="sxs-lookup"><span data-stu-id="207ba-118">\<system.Net> Element (Network Settings)</span></span>](system-net-element-network-settings.md)|<span data-ttu-id="207ba-119">Contém configurações que especificam como o .NET Framework se conecta à rede.</span><span class="sxs-lookup"><span data-stu-id="207ba-119">Contains settings that specify how the .NET Framework connects to the network.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="207ba-120">Exemplo</span><span class="sxs-lookup"><span data-stu-id="207ba-120">Example</span></span>  

 <span data-ttu-id="207ba-121">O exemplo a seguir especifica os parâmetros de SMTP apropriados para enviar email usando as credenciais de rede padrão.</span><span class="sxs-lookup"><span data-stu-id="207ba-121">The following example specifies the appropriate SMTP parameters to send email using the default network credentials.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="207ba-122">Confira também</span><span class="sxs-lookup"><span data-stu-id="207ba-122">See also</span></span>

- <xref:System.Net.Mail.SmtpClient>
- [<span data-ttu-id="207ba-123">Esquema de configurações de rede</span><span class="sxs-lookup"><span data-stu-id="207ba-123">Network Settings Schema</span></span>](index.md)
