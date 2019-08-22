---
title: Elemento <authenticationModules> (Configurações de Rede)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#authenticationModules
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/authenticationModules
helpviewer_keywords:
- authenticationModules element
- <authenticationModules> element
ms.assetid: 10fcfaad-82ef-4692-871a-0aec9dfbe75e
ms.openlocfilehash: 6488bfcd97e27a184b4a8cd1498d1c60f32babda
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/21/2019
ms.locfileid: "69659480"
---
# <a name="authenticationmodules-element-network-settings"></a><span data-ttu-id="abab2-102">\<Elemento de > authenticationModules (configurações de rede)</span><span class="sxs-lookup"><span data-stu-id="abab2-102">\<authenticationModules> Element (Network Settings)</span></span>
<span data-ttu-id="abab2-103">Especifica os módulos usados para autenticar solicitações de rede.</span><span class="sxs-lookup"><span data-stu-id="abab2-103">Specifies modules used to authenticate network requests.</span></span>  
  
 <span data-ttu-id="abab2-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="abab2-104">\<configuration></span></span>  
<span data-ttu-id="abab2-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="abab2-105">\<system.net></span></span>  
<span data-ttu-id="abab2-106">\<authenticationModules></span><span class="sxs-lookup"><span data-stu-id="abab2-106">\<authenticationModules></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="abab2-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="abab2-107">Syntax</span></span>  
  
```xml  
<authenticationModules>   
</authenticationModules>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="abab2-108">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="abab2-108">Attributes and Elements</span></span>  
 <span data-ttu-id="abab2-109">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="abab2-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="abab2-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="abab2-110">Attributes</span></span>  
 <span data-ttu-id="abab2-111">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="abab2-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="abab2-112">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="abab2-112">Child Elements</span></span>  
  
|<span data-ttu-id="abab2-113">**Elemento**</span><span class="sxs-lookup"><span data-stu-id="abab2-113">**Element**</span></span>|<span data-ttu-id="abab2-114">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="abab2-114">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="abab2-115">add</span><span class="sxs-lookup"><span data-stu-id="abab2-115">add</span></span>](add-element-for-authenticationmodules-network-settings.md)|<span data-ttu-id="abab2-116">Adiciona um módulo de autenticação ao aplicativo.</span><span class="sxs-lookup"><span data-stu-id="abab2-116">Adds an authentication module to the application.</span></span>|  
|[<span data-ttu-id="abab2-117">clear</span><span class="sxs-lookup"><span data-stu-id="abab2-117">clear</span></span>](clear-element-for-authenticationmodules-network-settings.md)|<span data-ttu-id="abab2-118">Limpa todos os módulos de autenticação do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="abab2-118">Clears all authentication modules from the application.</span></span>|  
|[<span data-ttu-id="abab2-119">remove</span><span class="sxs-lookup"><span data-stu-id="abab2-119">remove</span></span>](remove-element-for-authenticationmodules-network-settings.md)|<span data-ttu-id="abab2-120">Remove um módulo de autenticação do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="abab2-120">Removes an authentication module from the application.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="abab2-121">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="abab2-121">Parent Elements</span></span>  
  
|<span data-ttu-id="abab2-122">**Elemento**</span><span class="sxs-lookup"><span data-stu-id="abab2-122">**Element**</span></span>|<span data-ttu-id="abab2-123">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="abab2-123">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="abab2-124">system.net</span><span class="sxs-lookup"><span data-stu-id="abab2-124">system.net</span></span>](system-net-element-network-settings.md)|<span data-ttu-id="abab2-125">Contém configurações que especificam como o .NET Framework se conecta à rede.</span><span class="sxs-lookup"><span data-stu-id="abab2-125">Contains settings that specify how the .NET Framework connects to the network.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="abab2-126">Comentários</span><span class="sxs-lookup"><span data-stu-id="abab2-126">Remarks</span></span>  
 <span data-ttu-id="abab2-127">O `authenticationModule` elemento Especifica os módulos de autenticação que conduzem o processo de autenticação com um servidor.</span><span class="sxs-lookup"><span data-stu-id="abab2-127">The `authenticationModule` element specifies the authentication modules that conduct the authentication process with a server.</span></span> <span data-ttu-id="abab2-128">Um módulo de autenticação deve implementar <xref:System.Net.IAuthenticationModule> a interface.</span><span class="sxs-lookup"><span data-stu-id="abab2-128">An authentication module must implement the <xref:System.Net.IAuthenticationModule> interface.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="abab2-129">Arquivos de Configuração</span><span class="sxs-lookup"><span data-stu-id="abab2-129">Configuration Files</span></span>  
 <span data-ttu-id="abab2-130">Esse elemento pode ser usado no arquivo de configuração do aplicativo ou no arquivo de configuração do computador (Machine. config).</span><span class="sxs-lookup"><span data-stu-id="abab2-130">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="abab2-131">Exemplo</span><span class="sxs-lookup"><span data-stu-id="abab2-131">Example</span></span>  
 <span data-ttu-id="abab2-132">O exemplo a seguir habilita um módulo de autenticação.</span><span class="sxs-lookup"><span data-stu-id="abab2-132">The following example enables an authentication module.</span></span> <span data-ttu-id="abab2-133">Você deve substituir os valores de Version e PublicKeyToken pelos valores corretos para o módulo especificado.</span><span class="sxs-lookup"><span data-stu-id="abab2-133">You should replace the values for Version and PublicKeyToken with the correct values for the specified module.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <authenticationModules>  
      <add type="System.Net.DigestClient, System, Version=2.0.3600.0,  
                 Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
    </authenticationModules>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="abab2-134">Consulte também</span><span class="sxs-lookup"><span data-stu-id="abab2-134">See also</span></span>

- <xref:System.Net.IAuthenticationModule>
- <xref:System.Net.AuthenticationManager>
- [<span data-ttu-id="abab2-135">Esquema de configurações de rede</span><span class="sxs-lookup"><span data-stu-id="abab2-135">Network Settings Schema</span></span>](index.md)
