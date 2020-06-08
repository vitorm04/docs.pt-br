---
title: Elemento <add> para authenticationModules (Configurações de Rede)
description: O <add> elemento de configurações de rede para ConnectionManagement adiciona um endereço IP ou nome DNS à lista de gerenciamento de conexão no .NET Framework.
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
ms.openlocfilehash: 1a6d0f79f076a69cec33ac14f0e0f33f7c3c6577
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84504635"
---
# <a name="add-element-for-authenticationmodules-network-settings"></a><span data-ttu-id="0c1a1-103">Elemento \<add> para authenticationModules (Configurações de Rede)</span><span class="sxs-lookup"><span data-stu-id="0c1a1-103">\<add> Element for authenticationModules (Network Settings)</span></span>
<span data-ttu-id="0c1a1-104">Adiciona um módulo de autenticação ao aplicativo.</span><span class="sxs-lookup"><span data-stu-id="0c1a1-104">Adds an authentication module to the application.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<authenticationModules>**](authenticationmodules-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**

## <a name="syntax"></a><span data-ttu-id="0c1a1-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="0c1a1-105">Syntax</span></span>  
  
```xml  
<add
  type="type_fullname, assembly_fullname"
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0c1a1-106">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="0c1a1-106">Attributes and Elements</span></span>  
 <span data-ttu-id="0c1a1-107">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="0c1a1-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0c1a1-108">Atributos</span><span class="sxs-lookup"><span data-stu-id="0c1a1-108">Attributes</span></span>  
  
|<span data-ttu-id="0c1a1-109">**Atributo**</span><span class="sxs-lookup"><span data-stu-id="0c1a1-109">**Attribute**</span></span>|<span data-ttu-id="0c1a1-110">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="0c1a1-110">**Description**</span></span>|  
|-------------------|---------------------|  
|`type`|<span data-ttu-id="0c1a1-111">O nome do tipo totalmente qualificado (indicado pela <xref:System.Type.FullName%2A> Propriedade) e o nome do assembly (indicado pela <xref:System.Reflection.Assembly.FullName%2A> Propriedade), separados por uma vírgula.</span><span class="sxs-lookup"><span data-stu-id="0c1a1-111">The fully qualified type name (indicated by the <xref:System.Type.FullName%2A> property) and the assembly name (indicated by the <xref:System.Reflection.Assembly.FullName%2A> property), separated by a comma.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="0c1a1-112">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="0c1a1-112">Child Elements</span></span>  
 <span data-ttu-id="0c1a1-113">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="0c1a1-113">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="0c1a1-114">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="0c1a1-114">Parent Elements</span></span>  
  
|<span data-ttu-id="0c1a1-115">**Elemento**</span><span class="sxs-lookup"><span data-stu-id="0c1a1-115">**Element**</span></span>|<span data-ttu-id="0c1a1-116">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="0c1a1-116">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="0c1a1-117">authenticationModules</span><span class="sxs-lookup"><span data-stu-id="0c1a1-117">authenticationModules</span></span>](authenticationmodules-element-network-settings.md)|<span data-ttu-id="0c1a1-118">Especifica os módulos usados para autenticar solicitações de rede.</span><span class="sxs-lookup"><span data-stu-id="0c1a1-118">Specifies modules used to authenticate network requests.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0c1a1-119">Comentários</span><span class="sxs-lookup"><span data-stu-id="0c1a1-119">Remarks</span></span>  
 <span data-ttu-id="0c1a1-120">O `add` elemento adiciona um módulo de autenticação ao final da lista de módulos de autenticação registrados.</span><span class="sxs-lookup"><span data-stu-id="0c1a1-120">The `add` element adds an authentication module to the end of the list of registered authentication modules.</span></span> <span data-ttu-id="0c1a1-121">Os módulos de autenticação são chamados na ordem em que foram adicionados à lista.</span><span class="sxs-lookup"><span data-stu-id="0c1a1-121">Authentication modules are called in the order in which they were added to the list.</span></span>  
  
 <span data-ttu-id="0c1a1-122">O valor do `type` atributo deve ser um nome de tipo válido e um nome de assembly correspondente, separados por uma vírgula.</span><span class="sxs-lookup"><span data-stu-id="0c1a1-122">The value for the `type` attribute should be a valid type name and corresponding assembly name, separated by a comma.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="0c1a1-123">Arquivos de configuração</span><span class="sxs-lookup"><span data-stu-id="0c1a1-123">Configuration Files</span></span>  
 <span data-ttu-id="0c1a1-124">Esse elemento pode ser usado no arquivo de configuração do aplicativo ou no arquivo de configuração do computador (Machine. config).</span><span class="sxs-lookup"><span data-stu-id="0c1a1-124">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="0c1a1-125">Exemplo</span><span class="sxs-lookup"><span data-stu-id="0c1a1-125">Example</span></span>  
 <span data-ttu-id="0c1a1-126">O exemplo a seguir habilita os módulos de autenticação padrão.</span><span class="sxs-lookup"><span data-stu-id="0c1a1-126">The following example enables the default authentication modules.</span></span> <span data-ttu-id="0c1a1-127">Você deve substituir os valores de Version e PublicKeyToken pelos valores corretos para o módulo especificado.</span><span class="sxs-lookup"><span data-stu-id="0c1a1-127">You should replace the values for Version and PublicKeyToken with the correct values for the specified module.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="0c1a1-128">Confira também</span><span class="sxs-lookup"><span data-stu-id="0c1a1-128">See also</span></span>

- <xref:System.Net.IAuthenticationModule>
- <xref:System.Net.AuthenticationManager>
- [<span data-ttu-id="0c1a1-129">Esquema de configurações de rede</span><span class="sxs-lookup"><span data-stu-id="0c1a1-129">Network Settings Schema</span></span>](index.md)
