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
ms.openlocfilehash: 4181a045079bdb455a63ebda722dd6b0daf33c4d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79155109"
---
# <a name="add-element-for-authenticationmodules-network-settings"></a><span data-ttu-id="30040-102">\<adicionar> Elemento para autenticaçãoMódulos (Configurações de rede)</span><span class="sxs-lookup"><span data-stu-id="30040-102">\<add> Element for authenticationModules (Network Settings)</span></span>
<span data-ttu-id="30040-103">Adiciona um módulo de autenticação ao aplicativo.</span><span class="sxs-lookup"><span data-stu-id="30040-103">Adds an authentication module to the application.</span></span>  

<span data-ttu-id="30040-104">[**\<>de configuração**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="30040-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="30040-105">&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="30040-105">&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)</span></span>\
<span data-ttu-id="30040-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<autenticaçãoMódulos>**](authenticationmodules-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="30040-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<authenticationModules>**](authenticationmodules-element-network-settings.md)</span></span>\
<span data-ttu-id="30040-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<adicionar>**</span><span class="sxs-lookup"><span data-stu-id="30040-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**</span></span>

## <a name="syntax"></a><span data-ttu-id="30040-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="30040-108">Syntax</span></span>  
  
```xml  
<add
  type="type_fullname, assembly_fullname"
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="30040-109">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="30040-109">Attributes and Elements</span></span>  
 <span data-ttu-id="30040-110">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="30040-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="30040-111">Atributos</span><span class="sxs-lookup"><span data-stu-id="30040-111">Attributes</span></span>  
  
|<span data-ttu-id="30040-112">**Atributo**</span><span class="sxs-lookup"><span data-stu-id="30040-112">**Attribute**</span></span>|<span data-ttu-id="30040-113">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="30040-113">**Description**</span></span>|  
|-------------------|---------------------|  
|`type`|<span data-ttu-id="30040-114">O nome do tipo totalmente <xref:System.Type.FullName%2A> qualificado (indicado pela propriedade) e <xref:System.Reflection.Assembly.FullName%2A> o nome de montagem (indicado pela propriedade), separados por uma comma.</span><span class="sxs-lookup"><span data-stu-id="30040-114">The fully qualified type name (indicated by the <xref:System.Type.FullName%2A> property) and the assembly name (indicated by the <xref:System.Reflection.Assembly.FullName%2A> property), separated by a comma.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="30040-115">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="30040-115">Child Elements</span></span>  
 <span data-ttu-id="30040-116">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="30040-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="30040-117">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="30040-117">Parent Elements</span></span>  
  
|<span data-ttu-id="30040-118">**Elemento**</span><span class="sxs-lookup"><span data-stu-id="30040-118">**Element**</span></span>|<span data-ttu-id="30040-119">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="30040-119">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="30040-120">authenticationModules</span><span class="sxs-lookup"><span data-stu-id="30040-120">authenticationModules</span></span>](authenticationmodules-element-network-settings.md)|<span data-ttu-id="30040-121">Especifica módulos usados para autenticar solicitações de rede.</span><span class="sxs-lookup"><span data-stu-id="30040-121">Specifies modules used to authenticate network requests.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="30040-122">Comentários</span><span class="sxs-lookup"><span data-stu-id="30040-122">Remarks</span></span>  
 <span data-ttu-id="30040-123">O `add` elemento adiciona um módulo de autenticação ao final da lista de módulos de autenticação registrados.</span><span class="sxs-lookup"><span data-stu-id="30040-123">The `add` element adds an authentication module to the end of the list of registered authentication modules.</span></span> <span data-ttu-id="30040-124">Os módulos de autenticação são chamados na ordem em que foram adicionados à lista.</span><span class="sxs-lookup"><span data-stu-id="30040-124">Authentication modules are called in the order in which they were added to the list.</span></span>  
  
 <span data-ttu-id="30040-125">O valor `type` para o atributo deve ser um nome de tipo válido e nome de montagem correspondente, separado por uma comuma.</span><span class="sxs-lookup"><span data-stu-id="30040-125">The value for the `type` attribute should be a valid type name and corresponding assembly name, separated by a comma.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="30040-126">Arquivos de configuração</span><span class="sxs-lookup"><span data-stu-id="30040-126">Configuration Files</span></span>  
 <span data-ttu-id="30040-127">Esse elemento pode ser usado no arquivo de configuração do aplicativo ou no arquivo de configuração da máquina (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="30040-127">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="30040-128">Exemplo</span><span class="sxs-lookup"><span data-stu-id="30040-128">Example</span></span>  
 <span data-ttu-id="30040-129">O exemplo a seguir permite os módulos de autenticação padrão.</span><span class="sxs-lookup"><span data-stu-id="30040-129">The following example enables the default authentication modules.</span></span> <span data-ttu-id="30040-130">Você deve substituir os valores de Versão e PublicKeyToken pelos valores corretos para o módulo especificado.</span><span class="sxs-lookup"><span data-stu-id="30040-130">You should replace the values for Version and PublicKeyToken with the correct values for the specified module.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="30040-131">Confira também</span><span class="sxs-lookup"><span data-stu-id="30040-131">See also</span></span>

- <xref:System.Net.IAuthenticationModule>
- <xref:System.Net.AuthenticationManager>
- [<span data-ttu-id="30040-132">Esquema de configurações de rede</span><span class="sxs-lookup"><span data-stu-id="30040-132">Network Settings Schema</span></span>](index.md)
