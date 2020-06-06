---
title: Elemento <useLegacyJit>
ms.date: 04/26/2017
ms.assetid: c2cf97f0-9262-4f1f-a754-5568b51110ad
ms.openlocfilehash: a126b8c0050a8d1fd96a3d090f9b018a9faa07a7
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/06/2020
ms.locfileid: "73968853"
---
# <a name="uselegacyjit-element"></a><span data-ttu-id="8e2e9-102">Elemento \<useLegacyJit></span><span class="sxs-lookup"><span data-stu-id="8e2e9-102">\<useLegacyJit> Element</span></span>

<span data-ttu-id="8e2e9-103">Determina se o Common Language Runtime usa o compilador JIT de 64 bits herdado para uma compilação just-in-time.</span><span class="sxs-lookup"><span data-stu-id="8e2e9-103">Determines whether the common language runtime uses the legacy 64-bit JIT compiler for just-in-time compilation.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<useLegacyJit>**  
  
## <a name="syntax"></a><span data-ttu-id="8e2e9-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="8e2e9-104">Syntax</span></span>  
  
```xml
<useLegacyJit enabled=0|1 />
```

<span data-ttu-id="8e2e9-105">O nome do elemento diferencia `useLegacyJit` maiúsculas de minúsculas.</span><span class="sxs-lookup"><span data-stu-id="8e2e9-105">The element name `useLegacyJit` is case-sensitive.</span></span>
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8e2e9-106">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="8e2e9-106">Attributes and elements</span></span>

<span data-ttu-id="8e2e9-107">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="8e2e9-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8e2e9-108">Atributos</span><span class="sxs-lookup"><span data-stu-id="8e2e9-108">Attributes</span></span>  
  
| <span data-ttu-id="8e2e9-109">Atributo</span><span class="sxs-lookup"><span data-stu-id="8e2e9-109">Attribute</span></span> | <span data-ttu-id="8e2e9-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="8e2e9-110">Description</span></span>                                                                                   |  
| --------- | --------------------------------------------------------------------------------------------- |  
| `enabled` | <span data-ttu-id="8e2e9-111">Atributo obrigatório.</span><span class="sxs-lookup"><span data-stu-id="8e2e9-111">Required attribute.</span></span><br><br><span data-ttu-id="8e2e9-112">Especifica se o tempo de execução usa o compilador JIT de 64 bits herdado.</span><span class="sxs-lookup"><span data-stu-id="8e2e9-112">Specifies whether the runtime uses the legacy 64-bit JIT compiler.</span></span> |  
  
### <a name="enabled-attribute"></a><span data-ttu-id="8e2e9-113">atributo habilitado</span><span class="sxs-lookup"><span data-stu-id="8e2e9-113">enabled attribute</span></span>  
  
| <span data-ttu-id="8e2e9-114">Valor</span><span class="sxs-lookup"><span data-stu-id="8e2e9-114">Value</span></span> | <span data-ttu-id="8e2e9-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="8e2e9-115">Description</span></span>                                                                                                         |  
| ----- | ------------------------------------------------------------------------------------------------------------------- |  
| <span data-ttu-id="8e2e9-116">0</span><span class="sxs-lookup"><span data-stu-id="8e2e9-116">0</span></span>     | <span data-ttu-id="8e2e9-117">O Common Language Runtime usa o novo compilador JIT de 64 bits incluído no .NET Framework 4,6 e versões posteriores.</span><span class="sxs-lookup"><span data-stu-id="8e2e9-117">The common language runtime uses the new 64-bit JIT compiler included in the .NET Framework 4.6 and later versions.</span></span> |  
| <span data-ttu-id="8e2e9-118">1</span><span class="sxs-lookup"><span data-stu-id="8e2e9-118">1</span></span>     | <span data-ttu-id="8e2e9-119">O Common Language Runtime usa o compilador JIT de 64 bits mais antigo.</span><span class="sxs-lookup"><span data-stu-id="8e2e9-119">The common language runtime uses the older 64-bit JIT compiler.</span></span>                                                     |  
  
### <a name="child-elements"></a><span data-ttu-id="8e2e9-120">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="8e2e9-120">Child elements</span></span>

<span data-ttu-id="8e2e9-121">Nenhum</span><span class="sxs-lookup"><span data-stu-id="8e2e9-121">None</span></span>
  
### <a name="parent-elements"></a><span data-ttu-id="8e2e9-122">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="8e2e9-122">Parent elements</span></span>  
  
| <span data-ttu-id="8e2e9-123">Elemento</span><span class="sxs-lookup"><span data-stu-id="8e2e9-123">Element</span></span>         | <span data-ttu-id="8e2e9-124">Descrição</span><span class="sxs-lookup"><span data-stu-id="8e2e9-124">Description</span></span>                                                                                                       |  
| --------------- | ----------------------------------------------------------------------------------------------------------------- |  
| `configuration` | <span data-ttu-id="8e2e9-125">O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="8e2e9-125">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span> |  
| `runtime`       | <span data-ttu-id="8e2e9-126">Contém informações sobre opções de inicialização do runtime.</span><span class="sxs-lookup"><span data-stu-id="8e2e9-126">Contains information about runtime initialization options.</span></span>                                                        |  
  
## <a name="remarks"></a><span data-ttu-id="8e2e9-127">Comentários</span><span class="sxs-lookup"><span data-stu-id="8e2e9-127">Remarks</span></span>  

<span data-ttu-id="8e2e9-128">A partir do .NET Framework 4,6, o Common Language Runtime usa um novo compilador de 64 bits para compilação JIT (just-in-time) por padrão.</span><span class="sxs-lookup"><span data-stu-id="8e2e9-128">Starting with the .NET Framework 4.6, the common language runtime uses a new 64-bit compiler for Just-In-Time (JIT) compilation by default.</span></span> <span data-ttu-id="8e2e9-129">Em alguns casos, isso pode resultar em uma diferença no comportamento do código do aplicativo que foi compilado por JIT pela versão anterior do compilador JIT de 64 bits.</span><span class="sxs-lookup"><span data-stu-id="8e2e9-129">In some cases, this may result in a difference in behavior from application code that was JIT-compiled by the previous version of the 64-bit JIT compiler.</span></span> <span data-ttu-id="8e2e9-130">Ao definir o `enabled` atributo do `<useLegacyJit>` elemento como `1` , você pode desabilitar o novo compilador JIT de 64 bits e, em vez disso, compilar seu aplicativo usando o compilador JIT de 64 bits herdado.</span><span class="sxs-lookup"><span data-stu-id="8e2e9-130">By setting the `enabled` attribute of the `<useLegacyJit>` element to `1`, you can disable the new 64-bit JIT compiler and instead compile your app using the legacy 64-bit JIT compiler.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="8e2e9-131">O `<useLegacyJit>` elemento afeta apenas a compilação JIT de 64 bits.</span><span class="sxs-lookup"><span data-stu-id="8e2e9-131">The `<useLegacyJit>` element affects 64-bit JIT compilation only.</span></span> <span data-ttu-id="8e2e9-132">A compilação com o compilador JIT de 32 bits não é afetada.</span><span class="sxs-lookup"><span data-stu-id="8e2e9-132">Compilation with the 32-bit JIT compiler is unaffected.</span></span>  
  
<span data-ttu-id="8e2e9-133">Em vez de usar uma configuração de arquivo de configuração, você pode habilitar o compilador JIT de 64 bits herdado de duas outras maneiras:</span><span class="sxs-lookup"><span data-stu-id="8e2e9-133">Instead of using a configuration file setting, you can enable the legacy 64-bit JIT compiler in two other ways:</span></span>  
  
- <span data-ttu-id="8e2e9-134">Definindo uma variável de ambiente</span><span class="sxs-lookup"><span data-stu-id="8e2e9-134">Setting an environment variable</span></span>

  <span data-ttu-id="8e2e9-135">Defina a `COMPLUS_useLegacyJit` variável de ambiente como `0` (use o novo compilador jit de 64 bits) ou `1` (use o compilador JIT de 64 bits mais antigo):</span><span class="sxs-lookup"><span data-stu-id="8e2e9-135">Set the `COMPLUS_useLegacyJit` environment variable to either `0` (use the new 64-bit JIT compiler) or `1` (use the older 64-bit JIT compiler):</span></span>
  
  ```env  
  COMPLUS_useLegacyJit=0|1  
  ```  
  
  <span data-ttu-id="8e2e9-136">A variável de ambiente tem *escopo global*, o que significa que ele afeta todos os aplicativos executados no computador.</span><span class="sxs-lookup"><span data-stu-id="8e2e9-136">The environment variable has *global scope*, which means that it affects all applications run on the machine.</span></span> <span data-ttu-id="8e2e9-137">Se definido, ele pode ser substituído pela configuração do arquivo de configuração do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="8e2e9-137">If set, it can be overridden by the application configuration file setting.</span></span> <span data-ttu-id="8e2e9-138">O nome da variável de ambiente não diferencia maiúsculas de minúsculas.</span><span class="sxs-lookup"><span data-stu-id="8e2e9-138">The environment variable name is not case-sensitive.</span></span>
  
- <span data-ttu-id="8e2e9-139">Adicionando uma chave do registro</span><span class="sxs-lookup"><span data-stu-id="8e2e9-139">Adding a registry key</span></span>

  <span data-ttu-id="8e2e9-140">Você pode habilitar o compilador JIT de 64 bits herdado adicionando um `REG_DWORD` valor à `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework` `HKEY_CURRENT_USER\SOFTWARE\Microsoft\.NETFramework` chave ou no registro.</span><span class="sxs-lookup"><span data-stu-id="8e2e9-140">You can enable the legacy 64-bit JIT compiler by adding a `REG_DWORD` value to either the `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework` or `HKEY_CURRENT_USER\SOFTWARE\Microsoft\.NETFramework` key in the registry.</span></span> <span data-ttu-id="8e2e9-141">O valor é nomeado `useLegacyJit` .</span><span class="sxs-lookup"><span data-stu-id="8e2e9-141">The value is named `useLegacyJit`.</span></span> <span data-ttu-id="8e2e9-142">Se o valor for 0, o novo compilador será usado.</span><span class="sxs-lookup"><span data-stu-id="8e2e9-142">If the value is 0, the new compiler is used.</span></span> <span data-ttu-id="8e2e9-143">Se o valor for 1, o compilador JIT de 64 bits herdado será habilitado.</span><span class="sxs-lookup"><span data-stu-id="8e2e9-143">If the value is 1, the legacy 64-bit JIT compiler is enabled.</span></span> <span data-ttu-id="8e2e9-144">O nome do valor do registro não diferencia maiúsculas de minúsculas.</span><span class="sxs-lookup"><span data-stu-id="8e2e9-144">The registry value name is not case-sensitive.</span></span>
  
  <span data-ttu-id="8e2e9-145">Adicionar o valor à `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework` chave afeta todos os aplicativos em execução no computador.</span><span class="sxs-lookup"><span data-stu-id="8e2e9-145">Adding the value to the `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework` key affects all apps running on the machine.</span></span> <span data-ttu-id="8e2e9-146">Adicionar o valor à `HKEY_CURRENT_USER\SOFTWARE\Microsoft\.NETFramework` chave afeta todos os aplicativos executados pelo usuário atual.</span><span class="sxs-lookup"><span data-stu-id="8e2e9-146">Adding the value to the `HKEY_CURRENT_USER\SOFTWARE\Microsoft\.NETFramework` key affects all apps run by the current user.</span></span> <span data-ttu-id="8e2e9-147">Se um computador estiver configurado com várias contas de usuário, somente os aplicativos executados pelo usuário atual serão afetados, a menos que o valor seja adicionado às chaves do registro para outros usuários também.</span><span class="sxs-lookup"><span data-stu-id="8e2e9-147">If a machine is configured with multiple user accounts, only apps run by the current user are affected, unless the value is added to the registry keys for other users as well.</span></span> <span data-ttu-id="8e2e9-148">A adição do `<useLegacyJit>` elemento a um arquivo de configuração substitui as configurações do registro, se estiverem presentes.</span><span class="sxs-lookup"><span data-stu-id="8e2e9-148">Adding the `<useLegacyJit>` element to a configuration file overrides the registry settings, if they're present.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8e2e9-149">Exemplo</span><span class="sxs-lookup"><span data-stu-id="8e2e9-149">Example</span></span>  

<span data-ttu-id="8e2e9-150">O arquivo de configuração a seguir desabilita a compilação com o novo compilador JIT de 64 bits e, em vez disso, usa o compilador JIT de 64 bits herdado.</span><span class="sxs-lookup"><span data-stu-id="8e2e9-150">The following configuration file disables compilation with the new 64-bit JIT compiler and instead uses the legacy 64-bit JIT compiler.</span></span>  
  
```xml  
<?xml version ="1.0"?>  
<configuration>  
  <runtime>  
    <useLegacyJit enabled="1" />  
  </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="8e2e9-151">Confira também</span><span class="sxs-lookup"><span data-stu-id="8e2e9-151">See also</span></span>

- [<span data-ttu-id="8e2e9-152">\<runtime>Elementos</span><span class="sxs-lookup"><span data-stu-id="8e2e9-152">\<runtime> Element</span></span>](runtime-element.md)
- [<span data-ttu-id="8e2e9-153">\<configuration>Elementos</span><span class="sxs-lookup"><span data-stu-id="8e2e9-153">\<configuration> Element</span></span>](../configuration-element.md)
- [<span data-ttu-id="8e2e9-154">Mitigação: novo compilador JIT de 64 bits</span><span class="sxs-lookup"><span data-stu-id="8e2e9-154">Mitigation: New 64-bit JIT Compiler</span></span>](../../../migration-guide/mitigation-new-64-bit-jit-compiler.md)
