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
ms.openlocfilehash: d72371921a85ff5a68dd9017f0fe8cf5d28557dd
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/21/2019
ms.locfileid: "69664246"
---
# <a name="add-element-for-authenticationmodules-network-settings"></a><span data-ttu-id="44306-102">\<Adicionar > elemento para authenticationModules (configurações de rede)</span><span class="sxs-lookup"><span data-stu-id="44306-102">\<add> Element for authenticationModules (Network Settings)</span></span>
<span data-ttu-id="44306-103">Adiciona um módulo de autenticação ao aplicativo.</span><span class="sxs-lookup"><span data-stu-id="44306-103">Adds an authentication module to the application.</span></span>  
  
 <span data-ttu-id="44306-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="44306-104">\<configuration></span></span>  
<span data-ttu-id="44306-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="44306-105">\<system.net></span></span>  
<span data-ttu-id="44306-106">\<authenticationModules></span><span class="sxs-lookup"><span data-stu-id="44306-106">\<authenticationModules></span></span>  
<span data-ttu-id="44306-107">\<add></span><span class="sxs-lookup"><span data-stu-id="44306-107">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="44306-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="44306-108">Syntax</span></span>  
  
```xml  
<add
  type="type_fullname, assembly_fullname"   
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="44306-109">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="44306-109">Attributes and Elements</span></span>  
 <span data-ttu-id="44306-110">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="44306-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="44306-111">Atributos</span><span class="sxs-lookup"><span data-stu-id="44306-111">Attributes</span></span>  
  
|<span data-ttu-id="44306-112">**Atributo**</span><span class="sxs-lookup"><span data-stu-id="44306-112">**Attribute**</span></span>|<span data-ttu-id="44306-113">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="44306-113">**Description**</span></span>|  
|-------------------|---------------------|  
|`type`|<span data-ttu-id="44306-114">O nome do tipo totalmente qualificado (indicado pela <xref:System.Type.FullName%2A> Propriedade) e o nome do assembly (indicado <xref:System.Reflection.Assembly.FullName%2A> pela propriedade), separados por uma vírgula.</span><span class="sxs-lookup"><span data-stu-id="44306-114">The fully qualified type name (indicated by the <xref:System.Type.FullName%2A> property) and the assembly name (indicated by the <xref:System.Reflection.Assembly.FullName%2A> property), separated by a comma.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="44306-115">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="44306-115">Child Elements</span></span>  
 <span data-ttu-id="44306-116">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="44306-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="44306-117">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="44306-117">Parent Elements</span></span>  
  
|<span data-ttu-id="44306-118">**Elemento**</span><span class="sxs-lookup"><span data-stu-id="44306-118">**Element**</span></span>|<span data-ttu-id="44306-119">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="44306-119">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="44306-120">authenticationModules</span><span class="sxs-lookup"><span data-stu-id="44306-120">authenticationModules</span></span>](authenticationmodules-element-network-settings.md)|<span data-ttu-id="44306-121">Especifica os módulos usados para autenticar solicitações de rede.</span><span class="sxs-lookup"><span data-stu-id="44306-121">Specifies modules used to authenticate network requests.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="44306-122">Comentários</span><span class="sxs-lookup"><span data-stu-id="44306-122">Remarks</span></span>  
 <span data-ttu-id="44306-123">O `add` elemento adiciona um módulo de autenticação ao final da lista de módulos de autenticação registrados.</span><span class="sxs-lookup"><span data-stu-id="44306-123">The `add` element adds an authentication module to the end of the list of registered authentication modules.</span></span> <span data-ttu-id="44306-124">Os módulos de autenticação são chamados na ordem em que foram adicionados à lista.</span><span class="sxs-lookup"><span data-stu-id="44306-124">Authentication modules are called in the order in which they were added to the list.</span></span>  
  
 <span data-ttu-id="44306-125">O valor do `type` atributo deve ser um nome de tipo válido e um nome de assembly correspondente, separados por uma vírgula.</span><span class="sxs-lookup"><span data-stu-id="44306-125">The value for the `type` attribute should be a valid type name and corresponding assembly name, separated by a comma.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="44306-126">Arquivos de Configuração</span><span class="sxs-lookup"><span data-stu-id="44306-126">Configuration Files</span></span>  
 <span data-ttu-id="44306-127">Esse elemento pode ser usado no arquivo de configuração do aplicativo ou no arquivo de configuração do computador (Machine. config).</span><span class="sxs-lookup"><span data-stu-id="44306-127">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="44306-128">Exemplo</span><span class="sxs-lookup"><span data-stu-id="44306-128">Example</span></span>  
 <span data-ttu-id="44306-129">O exemplo a seguir habilita os módulos de autenticação padrão.</span><span class="sxs-lookup"><span data-stu-id="44306-129">The following example enables the default authentication modules.</span></span> <span data-ttu-id="44306-130">Você deve substituir os valores de Version e PublicKeyToken pelos valores corretos para o módulo especificado.</span><span class="sxs-lookup"><span data-stu-id="44306-130">You should replace the values for Version and PublicKeyToken with the correct values for the specified module.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="44306-131">Consulte também</span><span class="sxs-lookup"><span data-stu-id="44306-131">See also</span></span>

- <xref:System.Net.IAuthenticationModule>
- <xref:System.Net.AuthenticationManager>
- [<span data-ttu-id="44306-132">Esquema de configurações de rede</span><span class="sxs-lookup"><span data-stu-id="44306-132">Network Settings Schema</span></span>](index.md)
