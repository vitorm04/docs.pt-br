---
title: '&lt;Adicionar&gt; elemento authenticationModules (configurações de rede)'
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
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 471e36bb584164b851e7a06c0e682ba9872f7910
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32742894"
---
# <a name="ltaddgt-element-for-authenticationmodules-network-settings"></a><span data-ttu-id="521fc-102">&lt;Adicionar&gt; elemento authenticationModules (configurações de rede)</span><span class="sxs-lookup"><span data-stu-id="521fc-102">&lt;add&gt; Element for authenticationModules (Network Settings)</span></span>
<span data-ttu-id="521fc-103">Adiciona um módulo de autenticação para o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="521fc-103">Adds an authentication module to the application.</span></span>  
  
 <span data-ttu-id="521fc-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="521fc-104">\<configuration></span></span>  
<span data-ttu-id="521fc-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="521fc-105">\<system.net></span></span>  
<span data-ttu-id="521fc-106">\<authenticationModules ></span><span class="sxs-lookup"><span data-stu-id="521fc-106">\<authenticationModules></span></span>  
<span data-ttu-id="521fc-107">\<add></span><span class="sxs-lookup"><span data-stu-id="521fc-107">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="521fc-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="521fc-108">Syntax</span></span>  
  
```xml  
<add
  type="type_fullname, assembly_fullname"   
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="521fc-109">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="521fc-109">Attributes and Elements</span></span>  
 <span data-ttu-id="521fc-110">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="521fc-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="521fc-111">Atributos</span><span class="sxs-lookup"><span data-stu-id="521fc-111">Attributes</span></span>  
  
|<span data-ttu-id="521fc-112">**Atributo**</span><span class="sxs-lookup"><span data-stu-id="521fc-112">**Attribute**</span></span>|<span data-ttu-id="521fc-113">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="521fc-113">**Description**</span></span>|  
|-------------------|---------------------|  
|`type`|<span data-ttu-id="521fc-114">O nome de tipo totalmente qualificado (indicado pelo <xref:System.Type.FullName%2A> propriedade) e o nome do assembly (indicado pelo <xref:System.Reflection.Assembly.FullName%2A> propriedade), separados por uma vírgula.</span><span class="sxs-lookup"><span data-stu-id="521fc-114">The fully qualified type name (indicated by the <xref:System.Type.FullName%2A> property) and the assembly name (indicated by the <xref:System.Reflection.Assembly.FullName%2A> property), separated by a comma.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="521fc-115">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="521fc-115">Child Elements</span></span>  
 <span data-ttu-id="521fc-116">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="521fc-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="521fc-117">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="521fc-117">Parent Elements</span></span>  
  
|<span data-ttu-id="521fc-118">**Elemento**</span><span class="sxs-lookup"><span data-stu-id="521fc-118">**Element**</span></span>|<span data-ttu-id="521fc-119">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="521fc-119">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="521fc-120">authenticationModules</span><span class="sxs-lookup"><span data-stu-id="521fc-120">authenticationModules</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/authenticationmodules-element-network-settings.md)|<span data-ttu-id="521fc-121">Especifica os módulos usados para autenticar solicitações de rede.</span><span class="sxs-lookup"><span data-stu-id="521fc-121">Specifies modules used to authenticate network requests.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="521fc-122">Comentários</span><span class="sxs-lookup"><span data-stu-id="521fc-122">Remarks</span></span>  
 <span data-ttu-id="521fc-123">O `add` elemento adiciona um módulo de autenticação ao final da lista de módulos de autenticação registrado.</span><span class="sxs-lookup"><span data-stu-id="521fc-123">The `add` element adds an authentication module to the end of the list of registered authentication modules.</span></span> <span data-ttu-id="521fc-124">Módulos de autenticação são chamados na ordem em que foram adicionados à lista.</span><span class="sxs-lookup"><span data-stu-id="521fc-124">Authentication modules are called in the order in which they were added to the list.</span></span>  
  
 <span data-ttu-id="521fc-125">O valor para o `type` atributo deve ser um nome de tipo válido e o nome de assembly correspondente, separados por uma vírgula.</span><span class="sxs-lookup"><span data-stu-id="521fc-125">The value for the `type` attribute should be a valid type name and corresponding assembly name, separated by a comma.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="521fc-126">Arquivos de Configuração</span><span class="sxs-lookup"><span data-stu-id="521fc-126">Configuration Files</span></span>  
 <span data-ttu-id="521fc-127">Esse elemento pode ser usado no arquivo de configuração do aplicativo ou o arquivo de configuração de máquina (Machine. config).</span><span class="sxs-lookup"><span data-stu-id="521fc-127">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="521fc-128">Exemplo</span><span class="sxs-lookup"><span data-stu-id="521fc-128">Example</span></span>  
 <span data-ttu-id="521fc-129">O exemplo a seguir permite que os módulos de autenticação padrão.</span><span class="sxs-lookup"><span data-stu-id="521fc-129">The following example enables the default authentication modules.</span></span> <span data-ttu-id="521fc-130">Você deve substituir os valores de versão e PublicKeyToken com os valores corretos para o módulo especificado.</span><span class="sxs-lookup"><span data-stu-id="521fc-130">You should replace the values for Version and PublicKeyToken with the correct values for the specified module.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="521fc-131">Consulte também</span><span class="sxs-lookup"><span data-stu-id="521fc-131">See Also</span></span>  
 <xref:System.Net.IAuthenticationModule>  
 <xref:System.Net.AuthenticationManager>  
 [<span data-ttu-id="521fc-132">Esquema de configurações de rede</span><span class="sxs-lookup"><span data-stu-id="521fc-132">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
