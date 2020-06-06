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
ms.openlocfilehash: b502cc4a0958f074018d4b0ce6b3fb118b811c2f
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/06/2020
ms.locfileid: "79154966"
---
# <a name="authenticationmodules-element-network-settings"></a><span data-ttu-id="dd8ab-102">Elemento \<authenticationModules> (Configurações de Rede)</span><span class="sxs-lookup"><span data-stu-id="dd8ab-102">\<authenticationModules> Element (Network Settings)</span></span>
<span data-ttu-id="dd8ab-103">Especifica os módulos usados para autenticar solicitações de rede.</span><span class="sxs-lookup"><span data-stu-id="dd8ab-103">Specifies modules used to authenticate network requests.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<authenticationModules>**

## <a name="syntax"></a><span data-ttu-id="dd8ab-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="dd8ab-104">Syntax</span></span>  
  
```xml  
<authenticationModules>
</authenticationModules>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="dd8ab-105">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="dd8ab-105">Attributes and Elements</span></span>  
 <span data-ttu-id="dd8ab-106">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="dd8ab-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="dd8ab-107">Atributos</span><span class="sxs-lookup"><span data-stu-id="dd8ab-107">Attributes</span></span>  
 <span data-ttu-id="dd8ab-108">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="dd8ab-108">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="dd8ab-109">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="dd8ab-109">Child Elements</span></span>  
  
|<span data-ttu-id="dd8ab-110">**Elemento**</span><span class="sxs-lookup"><span data-stu-id="dd8ab-110">**Element**</span></span>|<span data-ttu-id="dd8ab-111">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="dd8ab-111">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="dd8ab-112">adicionar</span><span class="sxs-lookup"><span data-stu-id="dd8ab-112">add</span></span>](add-element-for-authenticationmodules-network-settings.md)|<span data-ttu-id="dd8ab-113">Adiciona um módulo de autenticação ao aplicativo.</span><span class="sxs-lookup"><span data-stu-id="dd8ab-113">Adds an authentication module to the application.</span></span>|  
|[<span data-ttu-id="dd8ab-114">formatação</span><span class="sxs-lookup"><span data-stu-id="dd8ab-114">clear</span></span>](clear-element-for-authenticationmodules-network-settings.md)|<span data-ttu-id="dd8ab-115">Limpa todos os módulos de autenticação do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="dd8ab-115">Clears all authentication modules from the application.</span></span>|  
|[<span data-ttu-id="dd8ab-116">remove</span><span class="sxs-lookup"><span data-stu-id="dd8ab-116">remove</span></span>](remove-element-for-authenticationmodules-network-settings.md)|<span data-ttu-id="dd8ab-117">Remove um módulo de autenticação do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="dd8ab-117">Removes an authentication module from the application.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="dd8ab-118">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="dd8ab-118">Parent Elements</span></span>  
  
|<span data-ttu-id="dd8ab-119">**Elemento**</span><span class="sxs-lookup"><span data-stu-id="dd8ab-119">**Element**</span></span>|<span data-ttu-id="dd8ab-120">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="dd8ab-120">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="dd8ab-121">system.net</span><span class="sxs-lookup"><span data-stu-id="dd8ab-121">system.net</span></span>](system-net-element-network-settings.md)|<span data-ttu-id="dd8ab-122">Contém configurações que especificam como o .NET Framework se conecta à rede.</span><span class="sxs-lookup"><span data-stu-id="dd8ab-122">Contains settings that specify how the .NET Framework connects to the network.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="dd8ab-123">Comentários</span><span class="sxs-lookup"><span data-stu-id="dd8ab-123">Remarks</span></span>  
 <span data-ttu-id="dd8ab-124">O `authenticationModule` elemento Especifica os módulos de autenticação que conduzem o processo de autenticação com um servidor.</span><span class="sxs-lookup"><span data-stu-id="dd8ab-124">The `authenticationModule` element specifies the authentication modules that conduct the authentication process with a server.</span></span> <span data-ttu-id="dd8ab-125">Um módulo de autenticação deve implementar a <xref:System.Net.IAuthenticationModule> interface.</span><span class="sxs-lookup"><span data-stu-id="dd8ab-125">An authentication module must implement the <xref:System.Net.IAuthenticationModule> interface.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="dd8ab-126">Arquivos de configuração</span><span class="sxs-lookup"><span data-stu-id="dd8ab-126">Configuration Files</span></span>  
 <span data-ttu-id="dd8ab-127">Esse elemento pode ser usado no arquivo de configuração do aplicativo ou no arquivo de configuração do computador (Machine. config).</span><span class="sxs-lookup"><span data-stu-id="dd8ab-127">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="dd8ab-128">Exemplo</span><span class="sxs-lookup"><span data-stu-id="dd8ab-128">Example</span></span>  
 <span data-ttu-id="dd8ab-129">O exemplo a seguir habilita um módulo de autenticação.</span><span class="sxs-lookup"><span data-stu-id="dd8ab-129">The following example enables an authentication module.</span></span> <span data-ttu-id="dd8ab-130">Você deve substituir os valores de Version e PublicKeyToken pelos valores corretos para o módulo especificado.</span><span class="sxs-lookup"><span data-stu-id="dd8ab-130">You should replace the values for Version and PublicKeyToken with the correct values for the specified module.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="dd8ab-131">Confira também</span><span class="sxs-lookup"><span data-stu-id="dd8ab-131">See also</span></span>

- <xref:System.Net.IAuthenticationModule>
- <xref:System.Net.AuthenticationManager>
- [<span data-ttu-id="dd8ab-132">Esquema de configurações de rede</span><span class="sxs-lookup"><span data-stu-id="dd8ab-132">Network Settings Schema</span></span>](index.md)
