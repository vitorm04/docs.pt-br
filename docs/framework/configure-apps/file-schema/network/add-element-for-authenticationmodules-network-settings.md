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
ms.openlocfilehash: a46e6af97f37974805812fb0d19801d618eee4d4
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59105866"
---
# <a name="add-element-for-authenticationmodules-network-settings"></a><span data-ttu-id="a0577-102">\<Adicionar > elemento para authenticationModules (configurações de rede)</span><span class="sxs-lookup"><span data-stu-id="a0577-102">\<add> Element for authenticationModules (Network Settings)</span></span>
<span data-ttu-id="a0577-103">Adiciona um módulo de autenticação ao aplicativo.</span><span class="sxs-lookup"><span data-stu-id="a0577-103">Adds an authentication module to the application.</span></span>  
  
 <span data-ttu-id="a0577-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="a0577-104">\<configuration></span></span>  
<span data-ttu-id="a0577-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="a0577-105">\<system.net></span></span>  
<span data-ttu-id="a0577-106">\<authenticationModules></span><span class="sxs-lookup"><span data-stu-id="a0577-106">\<authenticationModules></span></span>  
<span data-ttu-id="a0577-107">\<add></span><span class="sxs-lookup"><span data-stu-id="a0577-107">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a0577-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a0577-108">Syntax</span></span>  
  
```xml  
<add
  type="type_fullname, assembly_fullname"   
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a0577-109">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="a0577-109">Attributes and Elements</span></span>  
 <span data-ttu-id="a0577-110">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="a0577-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a0577-111">Atributos</span><span class="sxs-lookup"><span data-stu-id="a0577-111">Attributes</span></span>  
  
|<span data-ttu-id="a0577-112">**Atributo**</span><span class="sxs-lookup"><span data-stu-id="a0577-112">**Attribute**</span></span>|<span data-ttu-id="a0577-113">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="a0577-113">**Description**</span></span>|  
|-------------------|---------------------|  
|`type`|<span data-ttu-id="a0577-114">O nome do tipo totalmente qualificado (indicado pelo <xref:System.Type.FullName%2A> propriedade) e o nome do assembly (indicado pelo <xref:System.Reflection.Assembly.FullName%2A> propriedade), separados por uma vírgula.</span><span class="sxs-lookup"><span data-stu-id="a0577-114">The fully qualified type name (indicated by the <xref:System.Type.FullName%2A> property) and the assembly name (indicated by the <xref:System.Reflection.Assembly.FullName%2A> property), separated by a comma.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a0577-115">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="a0577-115">Child Elements</span></span>  
 <span data-ttu-id="a0577-116">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="a0577-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="a0577-117">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="a0577-117">Parent Elements</span></span>  
  
|<span data-ttu-id="a0577-118">**Elemento**</span><span class="sxs-lookup"><span data-stu-id="a0577-118">**Element**</span></span>|<span data-ttu-id="a0577-119">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="a0577-119">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="a0577-120">authenticationModules</span><span class="sxs-lookup"><span data-stu-id="a0577-120">authenticationModules</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/authenticationmodules-element-network-settings.md)|<span data-ttu-id="a0577-121">Especifica os módulos usados para autenticar solicitações de rede.</span><span class="sxs-lookup"><span data-stu-id="a0577-121">Specifies modules used to authenticate network requests.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a0577-122">Comentários</span><span class="sxs-lookup"><span data-stu-id="a0577-122">Remarks</span></span>  
 <span data-ttu-id="a0577-123">O `add` elemento adiciona um módulo de autenticação para o final da lista de módulos de autenticação registrados.</span><span class="sxs-lookup"><span data-stu-id="a0577-123">The `add` element adds an authentication module to the end of the list of registered authentication modules.</span></span> <span data-ttu-id="a0577-124">Módulos de autenticação são chamados na ordem em que foram adicionados à lista.</span><span class="sxs-lookup"><span data-stu-id="a0577-124">Authentication modules are called in the order in which they were added to the list.</span></span>  
  
 <span data-ttu-id="a0577-125">O valor para o `type` atributo deve ser um nome de tipo válido e o nome do assembly correspondente, separados por vírgula.</span><span class="sxs-lookup"><span data-stu-id="a0577-125">The value for the `type` attribute should be a valid type name and corresponding assembly name, separated by a comma.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="a0577-126">Arquivos de Configuração</span><span class="sxs-lookup"><span data-stu-id="a0577-126">Configuration Files</span></span>  
 <span data-ttu-id="a0577-127">Esse elemento pode ser usado no arquivo de configuração do aplicativo ou o arquivo de configuração de máquina (Machine. config).</span><span class="sxs-lookup"><span data-stu-id="a0577-127">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="a0577-128">Exemplo</span><span class="sxs-lookup"><span data-stu-id="a0577-128">Example</span></span>  
 <span data-ttu-id="a0577-129">O exemplo a seguir permite que os módulos de autenticação padrão.</span><span class="sxs-lookup"><span data-stu-id="a0577-129">The following example enables the default authentication modules.</span></span> <span data-ttu-id="a0577-130">Você deve substituir os valores de versão e PublicKeyToken com os valores corretos para o módulo especificado.</span><span class="sxs-lookup"><span data-stu-id="a0577-130">You should replace the values for Version and PublicKeyToken with the correct values for the specified module.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="a0577-131">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a0577-131">See also</span></span>

- <xref:System.Net.IAuthenticationModule>
- <xref:System.Net.AuthenticationManager>
- [<span data-ttu-id="a0577-132">Esquema de configurações de rede</span><span class="sxs-lookup"><span data-stu-id="a0577-132">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
