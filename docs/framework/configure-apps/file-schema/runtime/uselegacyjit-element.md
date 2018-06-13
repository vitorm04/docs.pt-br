---
title: '&lt;useLegacyJit&gt; elemento'
ms.date: 04/26/2017
ms.assetid: c2cf97f0-9262-4f1f-a754-5568b51110ad
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: fd0ae1a44b41ddcae2149bcf685871a37dd01b06
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32746768"
---
# <a name="ltuselegacyjitgt-element"></a><span data-ttu-id="f5d41-102">&lt;useLegacyJit&gt; elemento</span><span class="sxs-lookup"><span data-stu-id="f5d41-102">&lt;useLegacyJit&gt; Element</span></span>

<span data-ttu-id="f5d41-103">Determina se o Common Language Runtime usa o compilador JIT de 64 bits herdado para uma compilação just-in-time.</span><span class="sxs-lookup"><span data-stu-id="f5d41-103">Determines whether the common language runtime uses the legacy 64-bit JIT compiler for just-in-time compilation.</span></span>  
  
<span data-ttu-id="f5d41-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="f5d41-104">\<configuration></span></span>  
<span data-ttu-id="f5d41-105">\<runtime></span><span class="sxs-lookup"><span data-stu-id="f5d41-105">\<runtime></span></span>  
<span data-ttu-id="f5d41-106">\<useLegacyJit ></span><span class="sxs-lookup"><span data-stu-id="f5d41-106">\<useLegacyJit></span></span>
  
## <a name="syntax"></a><span data-ttu-id="f5d41-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f5d41-107">Syntax</span></span>  
  
```xml
<useLegacyJit enabled=0|1 />
```

<span data-ttu-id="f5d41-108">O nome do elemento `useLegacyJit` diferencia maiusculas de minúsculas.</span><span class="sxs-lookup"><span data-stu-id="f5d41-108">The element name `useLegacyJit` is case-sensitive.</span></span>
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f5d41-109">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="f5d41-109">Attributes and elements</span></span>

<span data-ttu-id="f5d41-110">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="f5d41-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f5d41-111">Atributos</span><span class="sxs-lookup"><span data-stu-id="f5d41-111">Attributes</span></span>  
  
| <span data-ttu-id="f5d41-112">Atributo</span><span class="sxs-lookup"><span data-stu-id="f5d41-112">Attribute</span></span> | <span data-ttu-id="f5d41-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="f5d41-113">Description</span></span>                                                                                   |  
| --------- | --------------------------------------------------------------------------------------------- |  
| `enabled` | <span data-ttu-id="f5d41-114">Atributo obrigatório.</span><span class="sxs-lookup"><span data-stu-id="f5d41-114">Required attribute.</span></span><br><br><span data-ttu-id="f5d41-115">Especifica se o tempo de execução usa o compilador JIT 64-bit herdado.</span><span class="sxs-lookup"><span data-stu-id="f5d41-115">Specifies whether the runtime uses the legacy 64-bit JIT compiler.</span></span> |  
  
### <a name="enabled-attribute"></a><span data-ttu-id="f5d41-116">atributo habilitado</span><span class="sxs-lookup"><span data-stu-id="f5d41-116">enabled attribute</span></span>  
  
| <span data-ttu-id="f5d41-117">Valor</span><span class="sxs-lookup"><span data-stu-id="f5d41-117">Value</span></span> | <span data-ttu-id="f5d41-118">Descrição</span><span class="sxs-lookup"><span data-stu-id="f5d41-118">Description</span></span>                                                                                                         |  
| ----- | ------------------------------------------------------------------------------------------------------------------- |  
| <span data-ttu-id="f5d41-119">0</span><span class="sxs-lookup"><span data-stu-id="f5d41-119">0</span></span>     | <span data-ttu-id="f5d41-120">O common language runtime usa o novo compilador JIT de 64 bits incluído no .NET Framework 4.6 e versões posteriores.</span><span class="sxs-lookup"><span data-stu-id="f5d41-120">The common language runtime uses the new 64-bit JIT compiler included in the .NET Framework 4.6 and later versions.</span></span> |  
| <span data-ttu-id="f5d41-121">1</span><span class="sxs-lookup"><span data-stu-id="f5d41-121">1</span></span>     | <span data-ttu-id="f5d41-122">O common language runtime usa o compilador JIT de 64 bits mais antigo.</span><span class="sxs-lookup"><span data-stu-id="f5d41-122">The common language runtime uses the older 64-bit JIT compiler.</span></span>                                                     |  
  
### <a name="child-elements"></a><span data-ttu-id="f5d41-123">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="f5d41-123">Child elements</span></span>

<span data-ttu-id="f5d41-124">Nenhum</span><span class="sxs-lookup"><span data-stu-id="f5d41-124">None</span></span>
  
### <a name="parent-elements"></a><span data-ttu-id="f5d41-125">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="f5d41-125">Parent elements</span></span>  
  
| <span data-ttu-id="f5d41-126">Elemento</span><span class="sxs-lookup"><span data-stu-id="f5d41-126">Element</span></span>         | <span data-ttu-id="f5d41-127">Descrição</span><span class="sxs-lookup"><span data-stu-id="f5d41-127">Description</span></span>                                                                                                       |  
| --------------- | ----------------------------------------------------------------------------------------------------------------- |  
| `configuration` | <span data-ttu-id="f5d41-128">O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="f5d41-128">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span> |  
| `runtime`       | <span data-ttu-id="f5d41-129">Contém informações sobre opções de inicialização do tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="f5d41-129">Contains information about runtime initialization options.</span></span>                                                        |  
  
## <a name="remarks"></a><span data-ttu-id="f5d41-130">Comentários</span><span class="sxs-lookup"><span data-stu-id="f5d41-130">Remarks</span></span>  

<span data-ttu-id="f5d41-131">Começando com o .NET Framework 4.6, o common language runtime usa um novo compilador de 64 bits para compilação Just-in-(JIT) por padrão.</span><span class="sxs-lookup"><span data-stu-id="f5d41-131">Starting with the .NET Framework 4.6, the common language runtime uses a new 64-bit compiler for Just-In-Time (JIT) compilation by default.</span></span> <span data-ttu-id="f5d41-132">Em alguns casos, isso pode resultar em uma diferença no comportamento do código do aplicativo que foi compilado por JIT por versões anteriores do compilador JIT 64 bits.</span><span class="sxs-lookup"><span data-stu-id="f5d41-132">In some cases, this may result in a difference in behavior from application code that was JIT-compiled by the previous version of the 64-bit JIT compiler.</span></span> <span data-ttu-id="f5d41-133">Definindo o `enabled` atributo do `<useLegacyJit>` elemento `1`, você pode desabilitar o novo compilador JIT 64-bit e em vez disso, compile seu aplicativo usando o compilador JIT 64-bit herdado.</span><span class="sxs-lookup"><span data-stu-id="f5d41-133">By setting the `enabled` attribute of the `<useLegacyJit>` element to `1`, you can disable the new 64-bit JIT compiler and instead compile your app using the legacy 64-bit JIT compiler.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f5d41-134">O `<useLegacyJit>` elemento afeta apenas a compilação JIT em 64 bits.</span><span class="sxs-lookup"><span data-stu-id="f5d41-134">The `<useLegacyJit>` element affects 64-bit JIT compilation only.</span></span> <span data-ttu-id="f5d41-135">Compilação com o compilador JIT de 32 bits não é afetada.</span><span class="sxs-lookup"><span data-stu-id="f5d41-135">Compilation with the 32-bit JIT compiler is unaffected.</span></span>  
  
<span data-ttu-id="f5d41-136">Em vez de usar uma configuração de arquivo de configuração, você pode habilitar o compilador JIT herdado 64-bit em duas outras maneiras:</span><span class="sxs-lookup"><span data-stu-id="f5d41-136">Instead of using a configuration file setting, you can enable the legacy 64-bit JIT compiler in two other ways:</span></span>  
  
- <span data-ttu-id="f5d41-137">Definindo uma variável de ambiente</span><span class="sxs-lookup"><span data-stu-id="f5d41-137">Setting an environment variable</span></span>

  <span data-ttu-id="f5d41-138">Definir o `COMPLUS_useLegacyJit` variável de ambiente para o `0` (use o novo compilador JIT 64 bits) ou `1` (use o compilador JIT 64 bits mais antigo):</span><span class="sxs-lookup"><span data-stu-id="f5d41-138">Set the `COMPLUS_useLegacyJit` environment variable to either `0` (use the new 64-bit JIT compiler) or `1` (use the older 64-bit JIT compiler):</span></span>
  
  ```  
  COMPLUS_useLegacyJit=0|1  
  ```  
  
  <span data-ttu-id="f5d41-139">A variável de ambiente tem *escopo global*, que significa que ele afeta todos os aplicativos executados no computador.</span><span class="sxs-lookup"><span data-stu-id="f5d41-139">The environment variable has *global scope*, which means that it affects all applications run on the machine.</span></span> <span data-ttu-id="f5d41-140">Se definido, ele pode ser substituído pelo parâmetro de arquivo de configuração do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="f5d41-140">If set, it can be overridden by the application configuration file setting.</span></span> <span data-ttu-id="f5d41-141">O nome da variável de ambiente não diferencia maiusculas de minúsculas.</span><span class="sxs-lookup"><span data-stu-id="f5d41-141">The environment variable name is not case-sensitive.</span></span>
  
- <span data-ttu-id="f5d41-142">Adicionar uma chave do registro</span><span class="sxs-lookup"><span data-stu-id="f5d41-142">Adding a registry key</span></span>

  <span data-ttu-id="f5d41-143">Você pode habilitar o compilador JIT 64-bit herdado adicionando um `REG_DWORD` valor como o `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework` ou `HKEY_CURRENT_USER\SOFTWARE\Microsoft\.NETFramework` chave no registro.</span><span class="sxs-lookup"><span data-stu-id="f5d41-143">You can enable the legacy 64-bit JIT compiler by adding a `REG_DWORD` value to either the `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework` or `HKEY_CURRENT_USER\SOFTWARE\Microsoft\.NETFramework` key in the registry.</span></span> <span data-ttu-id="f5d41-144">O valor é denominado `useLegacyJit`.</span><span class="sxs-lookup"><span data-stu-id="f5d41-144">The value is named `useLegacyJit`.</span></span> <span data-ttu-id="f5d41-145">Se o valor for 0, o compilador novo será usado.</span><span class="sxs-lookup"><span data-stu-id="f5d41-145">If the value is 0, the new compiler is used.</span></span> <span data-ttu-id="f5d41-146">Se o valor for 1, o compilador JIT 64-bit herdado está habilitado.</span><span class="sxs-lookup"><span data-stu-id="f5d41-146">If the value is 1, the legacy 64-bit JIT compiler is enabled.</span></span> <span data-ttu-id="f5d41-147">O nome do valor do registro não diferencia maiusculas de minúsculas.</span><span class="sxs-lookup"><span data-stu-id="f5d41-147">The registry value name is not case-sensitive.</span></span>
  
  <span data-ttu-id="f5d41-148">Adicionando o valor para o `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework` chave afeta todos os aplicativos em execução no computador.</span><span class="sxs-lookup"><span data-stu-id="f5d41-148">Adding the value to the `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework` key affects all apps running on the machine.</span></span> <span data-ttu-id="f5d41-149">Adicionando o valor para o `HKEY_CURRENT_USER\SOFTWARE\Microsoft\.NETFramework` chave afeta todos os aplicativos executados pelo usuário atual.</span><span class="sxs-lookup"><span data-stu-id="f5d41-149">Adding the value to the `HKEY_CURRENT_USER\SOFTWARE\Microsoft\.NETFramework` key affects all apps run by the current user.</span></span> <span data-ttu-id="f5d41-150">Se um computador é configurado com várias contas de usuário, somente os aplicativos executados pelo usuário atual são afetados, a menos que o valor é adicionado para as chaves do registro para outros usuários.</span><span class="sxs-lookup"><span data-stu-id="f5d41-150">If a machine is configured with multiple user accounts, only apps run by the current user are affected, unless the value is added to the registry keys for other users as well.</span></span> <span data-ttu-id="f5d41-151">Adicionando o `<useLegacyJit>` elemento para um arquivo de configuração substitui as configurações do registro, se elas estiverem presentes.</span><span class="sxs-lookup"><span data-stu-id="f5d41-151">Adding the `<useLegacyJit>` element to a configuration file overrides the registry settings, if they're present.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f5d41-152">Exemplo</span><span class="sxs-lookup"><span data-stu-id="f5d41-152">Example</span></span>  

<span data-ttu-id="f5d41-153">O arquivo de configuração a seguir desabilita a compilação com o novo compilador JIT 64-bit e em vez disso, usa o compilador JIT 64-bit herdado.</span><span class="sxs-lookup"><span data-stu-id="f5d41-153">The following configuration file disables compilation with the new 64-bit JIT compiler and instead uses the legacy 64-bit JIT compiler.</span></span>  
  
```xml  
<?xml version ="1.0"?>  
<configuration>  
  <runtime>  
    <useLegacyJit enabled="1" />  
  </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="f5d41-154">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f5d41-154">See also</span></span>

<span data-ttu-id="f5d41-155">[\<tempo de execução > elemento](../../../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) </span><span class="sxs-lookup"><span data-stu-id="f5d41-155">[\<runtime> Element](../../../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) </span></span>  
<span data-ttu-id="f5d41-156">[\<Configuração > elemento](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="f5d41-156">[\<configuration> Element](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md) </span></span>  
[<span data-ttu-id="f5d41-157">Mitigação: novo compilador JIT de 64 bits</span><span class="sxs-lookup"><span data-stu-id="f5d41-157">Mitigation: New 64-bit JIT Compiler</span></span>](../../../../../docs/framework/migration-guide/mitigation-new-64-bit-jit-compiler.md)
