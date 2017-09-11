---
title: "Mitigação: novo compilador JIT de 64 bits"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-bcl
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- JIT compiler, 64-bit
- JIT compilation, 64-bit
- RyuJIT compiler
ms.assetid: 0332dabc-72c5-4bdc-8975-20d717802b17
caps.latest.revision: 6
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: b67c622531321e5cd1efa7db657d62d94c0f73e4
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---
# <a name="mitigation-new-64-bit-jit-compiler"></a><span data-ttu-id="d0154-102">Mitigação: novo compilador JIT de 64 bits</span><span class="sxs-lookup"><span data-stu-id="d0154-102">Mitigation: New 64-bit JIT Compiler</span></span>
<span data-ttu-id="d0154-103">A partir do .NET Framework 4.6, o tempo de execução inclui um novo compilador JIT de 64 bits para compilação just-in-time.</span><span class="sxs-lookup"><span data-stu-id="d0154-103">Starting with the .NET Framework 4.6, the runtime includes a new 64-bit JIT compiler for just-in-time compilation.</span></span> <span data-ttu-id="d0154-104">Essa alteração não afeta a compilação com o compilador JIT de 32 bits.</span><span class="sxs-lookup"><span data-stu-id="d0154-104">This change does not affect compilation with the  32-bit JIT compiler.</span></span>  
  
## <a name="unexpected-behavior-or-exceptions"></a><span data-ttu-id="d0154-105">Comportamento ou exceções inesperadas</span><span class="sxs-lookup"><span data-stu-id="d0154-105">Unexpected behavior or exceptions</span></span>  
 <span data-ttu-id="d0154-106">Em alguns casos, a compilação com o novo compilador JIT de 64 bits resulta em uma exceção de tempo de execução ou em um comportamento não observado durante a execução do código compilado pelo compilador JIT de 64 bits mais antigo.</span><span class="sxs-lookup"><span data-stu-id="d0154-106">In some cases, compilation with the new 64-bit JIT compiler results in a runtime exception or in behavior that is not observed when executing code compiled by the older 64-bit JIT compiler.</span></span> <span data-ttu-id="d0154-107">Os diferenças conhecidas incluem o seguinte:</span><span class="sxs-lookup"><span data-stu-id="d0154-107">The known differences include the following:</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="d0154-108">Todos esses problemas conhecidos foram resolvidos no novo compilador de 64 bits lançado com o .NET Framework 4.6.2.</span><span class="sxs-lookup"><span data-stu-id="d0154-108">All of these known issues have been addressed in the new 64-bit compiler released with the .NET Framework 4.6.2.</span></span> <span data-ttu-id="d0154-109">A maioria também foi resolvida nas versões de serviço do .NET Framework 4.6 e 4.6.1, incluídos com o Windows Update.</span><span class="sxs-lookup"><span data-stu-id="d0154-109">Most have also been addressed in service releases of the .NET Framework 4.6 and 4.6.1 that are included with Windows Update.</span></span> <span data-ttu-id="d0154-110">Você pode eliminar esses problemas garantindo que sua versão do Windows esteja atualizada, ou atualizando para o .NET Framework 4.6.2.</span><span class="sxs-lookup"><span data-stu-id="d0154-110">You can eliminate these issues by ensuring that your version of Windows is up to date, or by upgrading to the .NET Framework 4.6.2.</span></span>  
  
-   <span data-ttu-id="d0154-111">Sob certas condições, uma operação de conversão unboxing pode gerar uma <xref:System.NullReferenceException> em compilações de Versão com a otimização ativada.</span><span class="sxs-lookup"><span data-stu-id="d0154-111">Under certain conditions, an unboxing operation may throw a <xref:System.NullReferenceException> in Release builds with optimization turned on.</span></span>  
  
-   <span data-ttu-id="d0154-112">Em alguns casos, a execução do código de produção em um corpo de método grande pode gerar uma <xref:System.StackOverflowException>.</span><span class="sxs-lookup"><span data-stu-id="d0154-112">In some cases, execution of production code in a large method body may throw a <xref:System.StackOverflowException>.</span></span>  
  
-   <span data-ttu-id="d0154-113">Sob certas condições, as estruturas passadas para um método são tratadas como tipos de referência em vez de tipos de valor em compilações de Versão.</span><span class="sxs-lookup"><span data-stu-id="d0154-113">Under certain conditions, structures passed to a method are treated as reference types rather than value types in Release builds.</span></span> <span data-ttu-id="d0154-114">Um das manifestações desse problema é que os itens individuais em uma coleção aparecem em uma ordem inesperada.</span><span class="sxs-lookup"><span data-stu-id="d0154-114">One of the manifestations of this issue is that the individual items in a collection appear in an unexpected order.</span></span>  
  
-   <span data-ttu-id="d0154-115">Sob determinadas condições, a comparação de valores <xref:System.UInt16> com seu conjunto de bits alto será incorreta se a otimização estiver habilitada.</span><span class="sxs-lookup"><span data-stu-id="d0154-115">Under certain conditions, the comparison of <xref:System.UInt16> values with their high bit set is incorrect if optimization is enabled.</span></span>  
  
-   <span data-ttu-id="d0154-116">Sob certas condições, especialmente ao inicializar uma matriz de valores, a inicialização da memória pela instrução IL <xref:System.Reflection.Emit.OpCodes.Initblk?displayProperty=fullName> pode inicializar a memória com um valor incorreto.</span><span class="sxs-lookup"><span data-stu-id="d0154-116">Under certain conditions, particularly when initializing array values, memory initialization by the <xref:System.Reflection.Emit.OpCodes.Initblk?displayProperty=fullName> IL instruction may initialize memory with an incorrect value.</span></span> <span data-ttu-id="d0154-117">Isso pode resultar em uma saída incorreta ou uma exceção sem tratamento.</span><span class="sxs-lookup"><span data-stu-id="d0154-117">This can result either in an unhandled exception or incorrect output.</span></span>  
  
-   <span data-ttu-id="d0154-118">Sob certas condições raras, um teste de bits condicional poderá retornar o valor <xref:System.Boolean> incorreto ou gerar uma exceção se as otimizações do compilador estiverem habilitadas.</span><span class="sxs-lookup"><span data-stu-id="d0154-118">Under certain rare conditions, a conditional bit test can return the incorrect <xref:System.Boolean> value or throw an exception if compiler optimizations are enabled.</span></span>  
  
-   <span data-ttu-id="d0154-119">Sob certas condições, se uma instrução `if` for usada para testar uma condição antes de entrar em um bloco `try`, e na saída do bloco `try`, e a mesma condição for avaliada no bloco `catch` ou `finally`, o novo compilador JIT de 64 bits removerá a condição `if` do bloco `catch` ou `finally` durante a otimização do código.</span><span class="sxs-lookup"><span data-stu-id="d0154-119">Under certain conditions, if an `if` statement is used to test for a condition before entering  a `try` block and in the exit from the `try` block, and the same condition is evaluated in the `catch` or `finally` block, the new 64-bit JIT compiler removes the `if` condition from the `catch` or `finally` block when it optimizes code.</span></span> <span data-ttu-id="d0154-120">Como resultado, o código dentro da instrução `if` no bloco `catch` ou `finally` será executado incondicionalmente.</span><span class="sxs-lookup"><span data-stu-id="d0154-120">As a result, code inside the `if` statement in the `catch` or `finally` block is executed unconditionally.</span></span>  
  
<a name="General"></a>   
## <a name="mitigation-of-known-issues"></a><span data-ttu-id="d0154-121">Mitigação dos problemas conhecidos</span><span class="sxs-lookup"><span data-stu-id="d0154-121">Mitigation of known issues</span></span>  
 <span data-ttu-id="d0154-122">Se você encontrar os problemas listados acima, solucione-os seguindo um destes procedimentos:</span><span class="sxs-lookup"><span data-stu-id="d0154-122">If you encounter the issues listed above, you can address them by doing any of the following:</span></span>  
  
-   <span data-ttu-id="d0154-123">Atualizar para o .NET Framework 4.6.2.</span><span class="sxs-lookup"><span data-stu-id="d0154-123">Upgrade to the .NET Framework 4.6.2.</span></span> <span data-ttu-id="d0154-124">O novo compilador de 64 bits incluído com o .NET Framework 4.6.2 resolve cada um desses problemas conhecidos.</span><span class="sxs-lookup"><span data-stu-id="d0154-124">The new 64-bit compiler included with the .NET Framework 4.6.2 addresses each of these known issues.</span></span>  
  
-   <span data-ttu-id="d0154-125">Verifique se a sua versão do Windows está atualizada executando o Windows Update.</span><span class="sxs-lookup"><span data-stu-id="d0154-125">Ensure that your version of Windows is up to date by running Windows Update.</span></span> <span data-ttu-id="d0154-126">Atualizações de serviço para o .NET Framework 4.6 e 4.6.1 resolvem cada um desses problemas, exceto a <xref:System.NullReferenceException> em uma operação de conversão unboxing.</span><span class="sxs-lookup"><span data-stu-id="d0154-126">Service updates to the .NET Framework 4.6 and 4.6.1 address each of these issues except the <xref:System.NullReferenceException> in an unboxing operation.</span></span>  
  
-   <span data-ttu-id="d0154-127">Compilar com o compilador JIT de 64 bits mais antigo.</span><span class="sxs-lookup"><span data-stu-id="d0154-127">Compile with the older 64-bit JIT compiler.</span></span> <span data-ttu-id="d0154-128">Veja a seção [Mitigação de outros problemas](#Other) para saber mais sobre como fazer isso.</span><span class="sxs-lookup"><span data-stu-id="d0154-128">See the [Mitigation of other issues](#Other) section for more information on how to do this.</span></span>  
  
<a name="Other"></a>   
## <a name="mitigation-of-other-issues"></a><span data-ttu-id="d0154-129">Mitigação de outros problemas</span><span class="sxs-lookup"><span data-stu-id="d0154-129">Mitigation of other issues</span></span>  
 <span data-ttu-id="d0154-130">Se você encontrar qualquer outra diferença de comportamento entre o código compilado com o compilador de 64 bits mais antigo e o novo compilador JIT de 64 bits, ou entre as versões de depuração e de versão de seu aplicativo, ambas compiladas com o novo compilador JIT de 64 bits, faça o seguinte para compilar seu aplicativo com o compilador JIT de 64 bits mais antigo:</span><span class="sxs-lookup"><span data-stu-id="d0154-130">If you encounter any other difference in behavior between code compiled with the older 64-bit compiler and the new 64-bit JIT compiler, or between the debug and release versions of your app that are both compiled with the new 64-bit JIT compiler, you can do the following to compile your app with the older 64-bit JIT compiler:</span></span>  
  
-   <span data-ttu-id="d0154-131">Adicione a cada aplicativo o elemento [\<useLegacyJit>](../../../docs/framework/configure-apps/file-schema/runtime/uselegacyjit-element.md) ao arquivo de configuração do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="d0154-131">On a per-application basis, you can add the [\<useLegacyJit>](../../../docs/framework/configure-apps/file-schema/runtime/uselegacyjit-element.md) element to your application's configuration file.</span></span> <span data-ttu-id="d0154-132">Veja a seguir como desabilitar a compilação com o novo compilador JIT de 64 bits e usar, em vez disso, o compilador JIT de 64 bits herdado.</span><span class="sxs-lookup"><span data-stu-id="d0154-132">The following disables compilation with the new 64-bit JIT compiler and instead uses the legacy 64-bit JIT compiler.</span></span>  
  
    ```xml  
    <?xml version ="1.0"?>  
    <configuration>  
        <runtime>  
           <useLegacyJit enabled="1" />  
        </runtime>  
    </configuration>  
    ```  
  
-   <span data-ttu-id="d0154-133">Adicione a cada usuário um valor `REG_DWORD` denominado `useLegacyJit` para a chave `HKEY_CURRENT_USER\SOFTWARE\Microsoft\.NETFramework` do Registro.</span><span class="sxs-lookup"><span data-stu-id="d0154-133">On a per-user basis, you can add a `REG_DWORD` value named `useLegacyJit` to the `HKEY_CURRENT_USER\SOFTWARE\Microsoft\.NETFramework` key of the registry.</span></span> <span data-ttu-id="d0154-134">Um valor 1 habilita o compilador JIT de 64 bits herdado; um valor 0 o desabilita e habilita o novo compilador JIT de 64 bits.</span><span class="sxs-lookup"><span data-stu-id="d0154-134">A value of 1 enables the legacy 64-bit JIT compiler; a value of 0 disables it and enables the new 64-bit JIT compiler.</span></span>  
  
-   <span data-ttu-id="d0154-135">Adicione a cada máquina um valor `REG_DWORD` denominado `useLegacyJit` para a chave `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework` do Registro.</span><span class="sxs-lookup"><span data-stu-id="d0154-135">On a per-machine basis, you can add a `REG_DWORD` value named `useLegacyJit` to the `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework` key of the registry.</span></span> <span data-ttu-id="d0154-136">Um valor 1 habilita o compilador JIT de 64 bits herdado; um valor 0 o desabilita e habilita o novo compilador JIT de 64 bits.</span><span class="sxs-lookup"><span data-stu-id="d0154-136">A value of 1 enables the legacy 64-bit JIT compiler; a value of 0 disables it and enables the new 64-bit JIT compiler.</span></span>  
  
 <span data-ttu-id="d0154-137">Avise-nos sobre o problema relatando um bug no [Microsoft Connect](https://connect.microsoft.com/VisualStudio).</span><span class="sxs-lookup"><span data-stu-id="d0154-137">You can also let us know about the problem by reporting a bug on [Microsoft Connect](https://connect.microsoft.com/VisualStudio).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d0154-138">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d0154-138">See Also</span></span>  
 <span data-ttu-id="d0154-139">[Alterações no tempo de execução](../../../docs/framework/migration-guide/runtime-changes-in-the-net-framework-4-6.md) </span><span class="sxs-lookup"><span data-stu-id="d0154-139">[Runtime Changes](../../../docs/framework/migration-guide/runtime-changes-in-the-net-framework-4-6.md) </span></span>  
 [<span data-ttu-id="d0154-140">Elemento \<useLegacyJit></span><span class="sxs-lookup"><span data-stu-id="d0154-140">\<useLegacyJit> Element</span></span>](../../../docs/framework/configure-apps/file-schema/runtime/uselegacyjit-element.md)

