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
ms.openlocfilehash: bacaaf92464a355804a9ea8307f6e6f1caac1f05
ms.sourcegitcommit: 7f8eeef060ddeb2cabfa52843776faf652c5a1f5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/14/2019
ms.locfileid: "74087608"
---
# <a name="authenticationmodules-element-network-settings"></a><span data-ttu-id="e0148-102">\<elemento de > authenticationModules (configurações de rede)</span><span class="sxs-lookup"><span data-stu-id="e0148-102">\<authenticationModules> Element (Network Settings)</span></span>
<span data-ttu-id="e0148-103">Especifica os módulos usados para autenticar solicitações de rede.</span><span class="sxs-lookup"><span data-stu-id="e0148-103">Specifies modules used to authenticate network requests.</span></span>  

<span data-ttu-id="e0148-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="e0148-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="e0148-105">&nbsp;&nbsp;[ **\<System. net >** ](system-net-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="e0148-105">&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)</span></span>\
<span data-ttu-id="e0148-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<authenticationModules >**</span><span class="sxs-lookup"><span data-stu-id="e0148-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<authenticationModules>**</span></span>

## <a name="syntax"></a><span data-ttu-id="e0148-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e0148-107">Syntax</span></span>  
  
```xml  
<authenticationModules>   
</authenticationModules>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e0148-108">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="e0148-108">Attributes and Elements</span></span>  
 <span data-ttu-id="e0148-109">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="e0148-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e0148-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="e0148-110">Attributes</span></span>  
 <span data-ttu-id="e0148-111">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="e0148-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="e0148-112">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="e0148-112">Child Elements</span></span>  
  
|<span data-ttu-id="e0148-113">**Elemento**</span><span class="sxs-lookup"><span data-stu-id="e0148-113">**Element**</span></span>|<span data-ttu-id="e0148-114">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="e0148-114">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="e0148-115">add</span><span class="sxs-lookup"><span data-stu-id="e0148-115">add</span></span>](add-element-for-authenticationmodules-network-settings.md)|<span data-ttu-id="e0148-116">Adiciona um módulo de autenticação ao aplicativo.</span><span class="sxs-lookup"><span data-stu-id="e0148-116">Adds an authentication module to the application.</span></span>|  
|[<span data-ttu-id="e0148-117">clear</span><span class="sxs-lookup"><span data-stu-id="e0148-117">clear</span></span>](clear-element-for-authenticationmodules-network-settings.md)|<span data-ttu-id="e0148-118">Limpa todos os módulos de autenticação do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="e0148-118">Clears all authentication modules from the application.</span></span>|  
|[<span data-ttu-id="e0148-119">remove</span><span class="sxs-lookup"><span data-stu-id="e0148-119">remove</span></span>](remove-element-for-authenticationmodules-network-settings.md)|<span data-ttu-id="e0148-120">Remove um módulo de autenticação do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="e0148-120">Removes an authentication module from the application.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="e0148-121">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="e0148-121">Parent Elements</span></span>  
  
|<span data-ttu-id="e0148-122">**Elemento**</span><span class="sxs-lookup"><span data-stu-id="e0148-122">**Element**</span></span>|<span data-ttu-id="e0148-123">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="e0148-123">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="e0148-124">system.net</span><span class="sxs-lookup"><span data-stu-id="e0148-124">system.net</span></span>](system-net-element-network-settings.md)|<span data-ttu-id="e0148-125">Contém configurações que especificam como o .NET Framework se conecta à rede.</span><span class="sxs-lookup"><span data-stu-id="e0148-125">Contains settings that specify how the .NET Framework connects to the network.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e0148-126">Comentários</span><span class="sxs-lookup"><span data-stu-id="e0148-126">Remarks</span></span>  
 <span data-ttu-id="e0148-127">O elemento `authenticationModule` especifica os módulos de autenticação que conduzem o processo de autenticação com um servidor.</span><span class="sxs-lookup"><span data-stu-id="e0148-127">The `authenticationModule` element specifies the authentication modules that conduct the authentication process with a server.</span></span> <span data-ttu-id="e0148-128">Um módulo de autenticação deve implementar a interface <xref:System.Net.IAuthenticationModule>.</span><span class="sxs-lookup"><span data-stu-id="e0148-128">An authentication module must implement the <xref:System.Net.IAuthenticationModule> interface.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="e0148-129">Arquivos de Configuração</span><span class="sxs-lookup"><span data-stu-id="e0148-129">Configuration Files</span></span>  
 <span data-ttu-id="e0148-130">Esse elemento pode ser usado no arquivo de configuração do aplicativo ou no arquivo de configuração do computador (Machine. config).</span><span class="sxs-lookup"><span data-stu-id="e0148-130">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="e0148-131">Exemplo</span><span class="sxs-lookup"><span data-stu-id="e0148-131">Example</span></span>  
 <span data-ttu-id="e0148-132">O exemplo a seguir habilita um módulo de autenticação.</span><span class="sxs-lookup"><span data-stu-id="e0148-132">The following example enables an authentication module.</span></span> <span data-ttu-id="e0148-133">Você deve substituir os valores de Version e PublicKeyToken pelos valores corretos para o módulo especificado.</span><span class="sxs-lookup"><span data-stu-id="e0148-133">You should replace the values for Version and PublicKeyToken with the correct values for the specified module.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="e0148-134">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e0148-134">See also</span></span>

- <xref:System.Net.IAuthenticationModule>
- <xref:System.Net.AuthenticationManager>
- [<span data-ttu-id="e0148-135">Esquema de configurações de rede</span><span class="sxs-lookup"><span data-stu-id="e0148-135">Network Settings Schema</span></span>](index.md)
