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
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/06/2020
ms.locfileid: "79155109"
---
# <a name="add-element-for-authenticationmodules-network-settings"></a><span data-ttu-id="2bdc1-102">Elemento \<add> para authenticationModules (Configurações de Rede)</span><span class="sxs-lookup"><span data-stu-id="2bdc1-102">\<add> Element for authenticationModules (Network Settings)</span></span>
<span data-ttu-id="2bdc1-103">Adiciona um módulo de autenticação ao aplicativo.</span><span class="sxs-lookup"><span data-stu-id="2bdc1-103">Adds an authentication module to the application.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<authenticationModules>**](authenticationmodules-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**

## <a name="syntax"></a><span data-ttu-id="2bdc1-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="2bdc1-104">Syntax</span></span>  
  
```xml  
<add
  type="type_fullname, assembly_fullname"
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2bdc1-105">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="2bdc1-105">Attributes and Elements</span></span>  
 <span data-ttu-id="2bdc1-106">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="2bdc1-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2bdc1-107">Atributos</span><span class="sxs-lookup"><span data-stu-id="2bdc1-107">Attributes</span></span>  
  
|<span data-ttu-id="2bdc1-108">**Atributo**</span><span class="sxs-lookup"><span data-stu-id="2bdc1-108">**Attribute**</span></span>|<span data-ttu-id="2bdc1-109">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="2bdc1-109">**Description**</span></span>|  
|-------------------|---------------------|  
|`type`|<span data-ttu-id="2bdc1-110">O nome do tipo totalmente qualificado (indicado pela <xref:System.Type.FullName%2A> Propriedade) e o nome do assembly (indicado pela <xref:System.Reflection.Assembly.FullName%2A> Propriedade), separados por uma vírgula.</span><span class="sxs-lookup"><span data-stu-id="2bdc1-110">The fully qualified type name (indicated by the <xref:System.Type.FullName%2A> property) and the assembly name (indicated by the <xref:System.Reflection.Assembly.FullName%2A> property), separated by a comma.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="2bdc1-111">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="2bdc1-111">Child Elements</span></span>  
 <span data-ttu-id="2bdc1-112">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="2bdc1-112">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="2bdc1-113">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="2bdc1-113">Parent Elements</span></span>  
  
|<span data-ttu-id="2bdc1-114">**Elemento**</span><span class="sxs-lookup"><span data-stu-id="2bdc1-114">**Element**</span></span>|<span data-ttu-id="2bdc1-115">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="2bdc1-115">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="2bdc1-116">authenticationModules</span><span class="sxs-lookup"><span data-stu-id="2bdc1-116">authenticationModules</span></span>](authenticationmodules-element-network-settings.md)|<span data-ttu-id="2bdc1-117">Especifica os módulos usados para autenticar solicitações de rede.</span><span class="sxs-lookup"><span data-stu-id="2bdc1-117">Specifies modules used to authenticate network requests.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2bdc1-118">Comentários</span><span class="sxs-lookup"><span data-stu-id="2bdc1-118">Remarks</span></span>  
 <span data-ttu-id="2bdc1-119">O `add` elemento adiciona um módulo de autenticação ao final da lista de módulos de autenticação registrados.</span><span class="sxs-lookup"><span data-stu-id="2bdc1-119">The `add` element adds an authentication module to the end of the list of registered authentication modules.</span></span> <span data-ttu-id="2bdc1-120">Os módulos de autenticação são chamados na ordem em que foram adicionados à lista.</span><span class="sxs-lookup"><span data-stu-id="2bdc1-120">Authentication modules are called in the order in which they were added to the list.</span></span>  
  
 <span data-ttu-id="2bdc1-121">O valor do `type` atributo deve ser um nome de tipo válido e um nome de assembly correspondente, separados por uma vírgula.</span><span class="sxs-lookup"><span data-stu-id="2bdc1-121">The value for the `type` attribute should be a valid type name and corresponding assembly name, separated by a comma.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="2bdc1-122">Arquivos de configuração</span><span class="sxs-lookup"><span data-stu-id="2bdc1-122">Configuration Files</span></span>  
 <span data-ttu-id="2bdc1-123">Esse elemento pode ser usado no arquivo de configuração do aplicativo ou no arquivo de configuração do computador (Machine. config).</span><span class="sxs-lookup"><span data-stu-id="2bdc1-123">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="2bdc1-124">Exemplo</span><span class="sxs-lookup"><span data-stu-id="2bdc1-124">Example</span></span>  
 <span data-ttu-id="2bdc1-125">O exemplo a seguir habilita os módulos de autenticação padrão.</span><span class="sxs-lookup"><span data-stu-id="2bdc1-125">The following example enables the default authentication modules.</span></span> <span data-ttu-id="2bdc1-126">Você deve substituir os valores de Version e PublicKeyToken pelos valores corretos para o módulo especificado.</span><span class="sxs-lookup"><span data-stu-id="2bdc1-126">You should replace the values for Version and PublicKeyToken with the correct values for the specified module.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="2bdc1-127">Confira também</span><span class="sxs-lookup"><span data-stu-id="2bdc1-127">See also</span></span>

- <xref:System.Net.IAuthenticationModule>
- <xref:System.Net.AuthenticationManager>
- [<span data-ttu-id="2bdc1-128">Esquema de configurações de rede</span><span class="sxs-lookup"><span data-stu-id="2bdc1-128">Network Settings Schema</span></span>](index.md)
