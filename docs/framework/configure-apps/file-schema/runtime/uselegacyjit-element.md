---
title: Elemento <useLegacyJit>
ms.date: 04/26/2017
ms.assetid: c2cf97f0-9262-4f1f-a754-5568b51110ad
ms.openlocfilehash: 47aacb629dc234d9aeaab1ef6e6844fbbe5dbfdb
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73115104"
---
# <a name="uselegacyjit-element"></a><span data-ttu-id="54f48-102">\<Elemento useLegacyJit></span><span class="sxs-lookup"><span data-stu-id="54f48-102">\<useLegacyJit> Element</span></span>

<span data-ttu-id="54f48-103">Determina se o Common Language Runtime usa o compilador JIT de 64 bits herdado para uma compilação just-in-time.</span><span class="sxs-lookup"><span data-stu-id="54f48-103">Determines whether the common language runtime uses the legacy 64-bit JIT compiler for just-in-time compilation.</span></span>  
  
<span data-ttu-id="54f48-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="54f48-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="54f48-105">&nbsp; &nbsp;[ **\<runtime >** ](runtime-element.md) </span><span class="sxs-lookup"><span data-stu-id="54f48-105">&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)</span></span>\
<span data-ttu-id="54f48-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<useLegacyJit >**</span><span class="sxs-lookup"><span data-stu-id="54f48-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<useLegacyJit>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="54f48-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="54f48-107">Syntax</span></span>  
  
```xml
<useLegacyJit enabled=0|1 />
```

<span data-ttu-id="54f48-108">O nome do elemento `useLegacyJit` diferencia maiúsculas de minúsculas.</span><span class="sxs-lookup"><span data-stu-id="54f48-108">The element name `useLegacyJit` is case-sensitive.</span></span>
  
## <a name="attributes-and-elements"></a><span data-ttu-id="54f48-109">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="54f48-109">Attributes and elements</span></span>

<span data-ttu-id="54f48-110">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="54f48-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="54f48-111">Atributos</span><span class="sxs-lookup"><span data-stu-id="54f48-111">Attributes</span></span>  
  
| <span data-ttu-id="54f48-112">Atributo</span><span class="sxs-lookup"><span data-stu-id="54f48-112">Attribute</span></span> | <span data-ttu-id="54f48-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="54f48-113">Description</span></span>                                                                                   |  
| --------- | --------------------------------------------------------------------------------------------- |  
| `enabled` | <span data-ttu-id="54f48-114">Atributo obrigatório.</span><span class="sxs-lookup"><span data-stu-id="54f48-114">Required attribute.</span></span><br><br><span data-ttu-id="54f48-115">Especifica se o tempo de execução usa o compilador JIT de 64 bits herdado.</span><span class="sxs-lookup"><span data-stu-id="54f48-115">Specifies whether the runtime uses the legacy 64-bit JIT compiler.</span></span> |  
  
### <a name="enabled-attribute"></a><span data-ttu-id="54f48-116">atributo habilitado</span><span class="sxs-lookup"><span data-stu-id="54f48-116">enabled attribute</span></span>  
  
| <span data-ttu-id="54f48-117">Valor</span><span class="sxs-lookup"><span data-stu-id="54f48-117">Value</span></span> | <span data-ttu-id="54f48-118">Descrição</span><span class="sxs-lookup"><span data-stu-id="54f48-118">Description</span></span>                                                                                                         |  
| ----- | ------------------------------------------------------------------------------------------------------------------- |  
| <span data-ttu-id="54f48-119">0</span><span class="sxs-lookup"><span data-stu-id="54f48-119">0</span></span>     | <span data-ttu-id="54f48-120">O Common Language Runtime usa o novo compilador JIT de 64 bits incluído no .NET Framework 4,6 e versões posteriores.</span><span class="sxs-lookup"><span data-stu-id="54f48-120">The common language runtime uses the new 64-bit JIT compiler included in the .NET Framework 4.6 and later versions.</span></span> |  
| <span data-ttu-id="54f48-121">1</span><span class="sxs-lookup"><span data-stu-id="54f48-121">1</span></span>     | <span data-ttu-id="54f48-122">O Common Language Runtime usa o compilador JIT de 64 bits mais antigo.</span><span class="sxs-lookup"><span data-stu-id="54f48-122">The common language runtime uses the older 64-bit JIT compiler.</span></span>                                                     |  
  
### <a name="child-elements"></a><span data-ttu-id="54f48-123">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="54f48-123">Child elements</span></span>

<span data-ttu-id="54f48-124">Nenhum</span><span class="sxs-lookup"><span data-stu-id="54f48-124">None</span></span>
  
### <a name="parent-elements"></a><span data-ttu-id="54f48-125">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="54f48-125">Parent elements</span></span>  
  
| <span data-ttu-id="54f48-126">Elemento</span><span class="sxs-lookup"><span data-stu-id="54f48-126">Element</span></span>         | <span data-ttu-id="54f48-127">Descrição</span><span class="sxs-lookup"><span data-stu-id="54f48-127">Description</span></span>                                                                                                       |  
| --------------- | ----------------------------------------------------------------------------------------------------------------- |  
| `configuration` | <span data-ttu-id="54f48-128">O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="54f48-128">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span> |  
| `runtime`       | <span data-ttu-id="54f48-129">Contém informações sobre opções de inicialização do runtime.</span><span class="sxs-lookup"><span data-stu-id="54f48-129">Contains information about runtime initialization options.</span></span>                                                        |  
  
## <a name="remarks"></a><span data-ttu-id="54f48-130">Comentários</span><span class="sxs-lookup"><span data-stu-id="54f48-130">Remarks</span></span>  

<span data-ttu-id="54f48-131">A partir do .NET Framework 4,6, o Common Language Runtime usa um novo compilador de 64 bits para compilação JIT (just-in-time) por padrão.</span><span class="sxs-lookup"><span data-stu-id="54f48-131">Starting with the .NET Framework 4.6, the common language runtime uses a new 64-bit compiler for Just-In-Time (JIT) compilation by default.</span></span> <span data-ttu-id="54f48-132">Em alguns casos, isso pode resultar em uma diferença no comportamento do código do aplicativo que foi compilado por JIT pela versão anterior do compilador JIT de 64 bits.</span><span class="sxs-lookup"><span data-stu-id="54f48-132">In some cases, this may result in a difference in behavior from application code that was JIT-compiled by the previous version of the 64-bit JIT compiler.</span></span> <span data-ttu-id="54f48-133">Ao definir o atributo `enabled` do elemento `<useLegacyJit>` como `1`, você pode desabilitar o novo compilador JIT de 64 bits e, em vez disso, compilar seu aplicativo usando o compilador JIT de 64 bits herdado.</span><span class="sxs-lookup"><span data-stu-id="54f48-133">By setting the `enabled` attribute of the `<useLegacyJit>` element to `1`, you can disable the new 64-bit JIT compiler and instead compile your app using the legacy 64-bit JIT compiler.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="54f48-134">O elemento `<useLegacyJit>` afeta apenas a compilação JIT de 64 bits.</span><span class="sxs-lookup"><span data-stu-id="54f48-134">The `<useLegacyJit>` element affects 64-bit JIT compilation only.</span></span> <span data-ttu-id="54f48-135">A compilação com o compilador JIT de 32 bits não é afetada.</span><span class="sxs-lookup"><span data-stu-id="54f48-135">Compilation with the 32-bit JIT compiler is unaffected.</span></span>  
  
<span data-ttu-id="54f48-136">Em vez de usar uma configuração de arquivo de configuração, você pode habilitar o compilador JIT de 64 bits herdado de duas outras maneiras:</span><span class="sxs-lookup"><span data-stu-id="54f48-136">Instead of using a configuration file setting, you can enable the legacy 64-bit JIT compiler in two other ways:</span></span>  
  
- <span data-ttu-id="54f48-137">Definindo uma variável de ambiente</span><span class="sxs-lookup"><span data-stu-id="54f48-137">Setting an environment variable</span></span>

  <span data-ttu-id="54f48-138">Defina a variável de ambiente `COMPLUS_useLegacyJit` como `0` (use o novo compilador JIT de 64 bits) ou `1` (use o compilador JIT de 64 bits mais antigo):</span><span class="sxs-lookup"><span data-stu-id="54f48-138">Set the `COMPLUS_useLegacyJit` environment variable to either `0` (use the new 64-bit JIT compiler) or `1` (use the older 64-bit JIT compiler):</span></span>
  
  ```  
  COMPLUS_useLegacyJit=0|1  
  ```  
  
  <span data-ttu-id="54f48-139">A variável de ambiente tem *escopo global*, o que significa que ele afeta todos os aplicativos executados no computador.</span><span class="sxs-lookup"><span data-stu-id="54f48-139">The environment variable has *global scope*, which means that it affects all applications run on the machine.</span></span> <span data-ttu-id="54f48-140">Se definido, ele pode ser substituído pela configuração do arquivo de configuração do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="54f48-140">If set, it can be overridden by the application configuration file setting.</span></span> <span data-ttu-id="54f48-141">O nome da variável de ambiente não diferencia maiúsculas de minúsculas.</span><span class="sxs-lookup"><span data-stu-id="54f48-141">The environment variable name is not case-sensitive.</span></span>
  
- <span data-ttu-id="54f48-142">Adicionando uma chave do registro</span><span class="sxs-lookup"><span data-stu-id="54f48-142">Adding a registry key</span></span>

  <span data-ttu-id="54f48-143">Você pode habilitar o compilador JIT de 64 bits herdado adicionando um valor de `REG_DWORD` à `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework` ou `HKEY_CURRENT_USER\SOFTWARE\Microsoft\.NETFramework` chave no registro.</span><span class="sxs-lookup"><span data-stu-id="54f48-143">You can enable the legacy 64-bit JIT compiler by adding a `REG_DWORD` value to either the `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework` or `HKEY_CURRENT_USER\SOFTWARE\Microsoft\.NETFramework` key in the registry.</span></span> <span data-ttu-id="54f48-144">O valor é nomeado `useLegacyJit`.</span><span class="sxs-lookup"><span data-stu-id="54f48-144">The value is named `useLegacyJit`.</span></span> <span data-ttu-id="54f48-145">Se o valor for 0, o novo compilador será usado.</span><span class="sxs-lookup"><span data-stu-id="54f48-145">If the value is 0, the new compiler is used.</span></span> <span data-ttu-id="54f48-146">Se o valor for 1, o compilador JIT de 64 bits herdado será habilitado.</span><span class="sxs-lookup"><span data-stu-id="54f48-146">If the value is 1, the legacy 64-bit JIT compiler is enabled.</span></span> <span data-ttu-id="54f48-147">O nome do valor do registro não diferencia maiúsculas de minúsculas.</span><span class="sxs-lookup"><span data-stu-id="54f48-147">The registry value name is not case-sensitive.</span></span>
  
  <span data-ttu-id="54f48-148">Adicionar o valor à chave de `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework` afeta todos os aplicativos em execução no computador.</span><span class="sxs-lookup"><span data-stu-id="54f48-148">Adding the value to the `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework` key affects all apps running on the machine.</span></span> <span data-ttu-id="54f48-149">Adicionar o valor à chave de `HKEY_CURRENT_USER\SOFTWARE\Microsoft\.NETFramework` afeta todos os aplicativos executados pelo usuário atual.</span><span class="sxs-lookup"><span data-stu-id="54f48-149">Adding the value to the `HKEY_CURRENT_USER\SOFTWARE\Microsoft\.NETFramework` key affects all apps run by the current user.</span></span> <span data-ttu-id="54f48-150">Se um computador estiver configurado com várias contas de usuário, somente os aplicativos executados pelo usuário atual serão afetados, a menos que o valor seja adicionado às chaves do registro para outros usuários também.</span><span class="sxs-lookup"><span data-stu-id="54f48-150">If a machine is configured with multiple user accounts, only apps run by the current user are affected, unless the value is added to the registry keys for other users as well.</span></span> <span data-ttu-id="54f48-151">Adicionar o elemento `<useLegacyJit>` a um arquivo de configuração substitui as configurações do registro, se estiverem presentes.</span><span class="sxs-lookup"><span data-stu-id="54f48-151">Adding the `<useLegacyJit>` element to a configuration file overrides the registry settings, if they're present.</span></span>  
  
## <a name="example"></a><span data-ttu-id="54f48-152">Exemplo</span><span class="sxs-lookup"><span data-stu-id="54f48-152">Example</span></span>  

<span data-ttu-id="54f48-153">O arquivo de configuração a seguir desabilita a compilação com o novo compilador JIT de 64 bits e, em vez disso, usa o compilador JIT de 64 bits herdado.</span><span class="sxs-lookup"><span data-stu-id="54f48-153">The following configuration file disables compilation with the new 64-bit JIT compiler and instead uses the legacy 64-bit JIT compiler.</span></span>  
  
```xml  
<?xml version ="1.0"?>  
<configuration>  
  <runtime>  
    <useLegacyJit enabled="1" />  
  </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="54f48-154">Consulte também</span><span class="sxs-lookup"><span data-stu-id="54f48-154">See also</span></span>

- [<span data-ttu-id="54f48-155">Elemento > de tempo de execução \<</span><span class="sxs-lookup"><span data-stu-id="54f48-155">\<runtime> Element</span></span>](runtime-element.md)
- [<span data-ttu-id="54f48-156">Elemento \<configuration></span><span class="sxs-lookup"><span data-stu-id="54f48-156">\<configuration> Element</span></span>](../configuration-element.md)
- [<span data-ttu-id="54f48-157">Mitigação: novo compilador JIT de 64 bits</span><span class="sxs-lookup"><span data-stu-id="54f48-157">Mitigation: New 64-bit JIT Compiler</span></span>](../../../migration-guide/mitigation-new-64-bit-jit-compiler.md)
