---
title: Elemento <add> para authenticationModules (Configurações de Rede)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#add
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/authenticationModules/add
helpviewer_keywords:
- authenticationModules, add element
- add element, authenticationModules
- <authenticationModules>, add element
- <add> element, authenticationModules
ms.assetid: 333c5fb0-a2ab-4db8-8531-a7fe37bb9b5b
ms.openlocfilehash: 9c011cf1216b98fa20e330e185e4cf2c331b31d4
ms.sourcegitcommit: 7f8eeef060ddeb2cabfa52843776faf652c5a1f5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/14/2019
ms.locfileid: "74087945"
---
# <a name="add-element-for-authenticationmodules-network-settings"></a><span data-ttu-id="4373b-102">\<adicionar o elemento > para authenticationModules (configurações de rede)</span><span class="sxs-lookup"><span data-stu-id="4373b-102">\<add> Element for authenticationModules (Network Settings)</span></span>
<span data-ttu-id="4373b-103">Adiciona um módulo de autenticação ao aplicativo.</span><span class="sxs-lookup"><span data-stu-id="4373b-103">Adds an authentication module to the application.</span></span>  

<span data-ttu-id="4373b-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="4373b-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="4373b-105">&nbsp;&nbsp;[ **\<System. net >** ](system-net-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="4373b-105">&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)</span></span>\
<span data-ttu-id="4373b-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<authenticationModules >** ](authenticationmodules-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="4373b-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<authenticationModules>**](authenticationmodules-element-network-settings.md)</span></span>\
<span data-ttu-id="4373b-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\<**adicionar >**</span><span class="sxs-lookup"><span data-stu-id="4373b-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**</span></span>

## <a name="syntax"></a><span data-ttu-id="4373b-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="4373b-108">Syntax</span></span>  
  
```xml  
<add
  type="type_fullname, assembly_fullname"   
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4373b-109">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="4373b-109">Attributes and Elements</span></span>  
 <span data-ttu-id="4373b-110">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="4373b-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4373b-111">Atributos</span><span class="sxs-lookup"><span data-stu-id="4373b-111">Attributes</span></span>  
  
|<span data-ttu-id="4373b-112">**Attribute**</span><span class="sxs-lookup"><span data-stu-id="4373b-112">**Attribute**</span></span>|<span data-ttu-id="4373b-113">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="4373b-113">**Description**</span></span>|  
|-------------------|---------------------|  
|`type`|<span data-ttu-id="4373b-114">O nome do tipo totalmente qualificado (indicado pela propriedade <xref:System.Type.FullName%2A>) e o nome do assembly (indicado pela propriedade <xref:System.Reflection.Assembly.FullName%2A>), separados por uma vírgula.</span><span class="sxs-lookup"><span data-stu-id="4373b-114">The fully qualified type name (indicated by the <xref:System.Type.FullName%2A> property) and the assembly name (indicated by the <xref:System.Reflection.Assembly.FullName%2A> property), separated by a comma.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="4373b-115">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="4373b-115">Child Elements</span></span>  
 <span data-ttu-id="4373b-116">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="4373b-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="4373b-117">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="4373b-117">Parent Elements</span></span>  
  
|<span data-ttu-id="4373b-118">**Elemento**</span><span class="sxs-lookup"><span data-stu-id="4373b-118">**Element**</span></span>|<span data-ttu-id="4373b-119">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="4373b-119">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="4373b-120">authenticationModules</span><span class="sxs-lookup"><span data-stu-id="4373b-120">authenticationModules</span></span>](authenticationmodules-element-network-settings.md)|<span data-ttu-id="4373b-121">Especifica os módulos usados para autenticar solicitações de rede.</span><span class="sxs-lookup"><span data-stu-id="4373b-121">Specifies modules used to authenticate network requests.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4373b-122">Comentários</span><span class="sxs-lookup"><span data-stu-id="4373b-122">Remarks</span></span>  
 <span data-ttu-id="4373b-123">O elemento `add` adiciona um módulo de autenticação ao final da lista de módulos de autenticação registrados.</span><span class="sxs-lookup"><span data-stu-id="4373b-123">The `add` element adds an authentication module to the end of the list of registered authentication modules.</span></span> <span data-ttu-id="4373b-124">Os módulos de autenticação são chamados na ordem em que foram adicionados à lista.</span><span class="sxs-lookup"><span data-stu-id="4373b-124">Authentication modules are called in the order in which they were added to the list.</span></span>  
  
 <span data-ttu-id="4373b-125">O valor para o atributo `type` deve ser um nome de tipo válido e um nome de assembly correspondente, separados por uma vírgula.</span><span class="sxs-lookup"><span data-stu-id="4373b-125">The value for the `type` attribute should be a valid type name and corresponding assembly name, separated by a comma.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="4373b-126">Arquivos de Configuração</span><span class="sxs-lookup"><span data-stu-id="4373b-126">Configuration Files</span></span>  
 <span data-ttu-id="4373b-127">Esse elemento pode ser usado no arquivo de configuração do aplicativo ou no arquivo de configuração do computador (Machine. config).</span><span class="sxs-lookup"><span data-stu-id="4373b-127">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="4373b-128">Exemplo</span><span class="sxs-lookup"><span data-stu-id="4373b-128">Example</span></span>  
 <span data-ttu-id="4373b-129">O exemplo a seguir habilita os módulos de autenticação padrão.</span><span class="sxs-lookup"><span data-stu-id="4373b-129">The following example enables the default authentication modules.</span></span> <span data-ttu-id="4373b-130">Você deve substituir os valores de Version e PublicKeyToken pelos valores corretos para o módulo especificado.</span><span class="sxs-lookup"><span data-stu-id="4373b-130">You should replace the values for Version and PublicKeyToken with the correct values for the specified module.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
        <authenticationModules>  
            <add type="System.Net.DigestClient, System, Version=2.0.3600.0,  
                 Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
            <add type="System.Net.NegotiateClient, System, Version=2.0.3600.0,  
                 Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
            <add type="System.Net.KerberosClient, System, Version=2.0.3600.0,  
                 Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
            <add type="System.Net.NtlmClient, System, Version=2.0.3600.0,  
                 Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
            <add type="System.Net.BasicClient, System, Version=2.0.3600.0,  
                 Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
        </authenticationModules>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="4373b-131">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4373b-131">See also</span></span>

- <xref:System.Net.IAuthenticationModule>
- <xref:System.Net.AuthenticationManager>
- [<span data-ttu-id="4373b-132">Esquema de configurações de rede</span><span class="sxs-lookup"><span data-stu-id="4373b-132">Network Settings Schema</span></span>](index.md)
