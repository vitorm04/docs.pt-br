---
title: MDA bindingFailure
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- binding failure
- binding, failures
- MDAs (managed debugging assistants), binding failures
- assemblies [.NET Framework], binding failures
- managed debugging assistants (MDAs), binding failures
- BindingFailure MDA
ms.assetid: 26ada5af-175c-4576-931a-9f07fa1723e9
caps.latest.revision: 13
author: mairaw
ms.author: mairaw
manager: wpickett
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 4e78cdcc5bcf69902675fceacc9dac245bfec336
ms.contentlocale: pt-br
ms.lasthandoff: 08/21/2017

---
# <a name="bindingfailure-mda"></a><span data-ttu-id="87455-102">MDA bindingFailure</span><span class="sxs-lookup"><span data-stu-id="87455-102">bindingFailure MDA</span></span>
<span data-ttu-id="87455-103">O MDA (assistente para depuração gerenciada) `bindingFailure` é ativado quando um assembly falha ao ser carregado.</span><span class="sxs-lookup"><span data-stu-id="87455-103">The `bindingFailure` managed debugging assistant (MDA) is activated when an assembly fails to load.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="87455-104">Sintomas</span><span class="sxs-lookup"><span data-stu-id="87455-104">Symptoms</span></span>  
 <span data-ttu-id="87455-105">O código tentou carregar um assembly usando uma referência estática ou um dos métodos de carregador, como <xref:System.Reflection.Assembly.Load%2A?displayProperty=fullName> ou <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=fullName>.</span><span class="sxs-lookup"><span data-stu-id="87455-105">Code has attempted to load an assembly using a static reference or one of the loader methods, such as <xref:System.Reflection.Assembly.Load%2A?displayProperty=fullName> or <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=fullName>.</span></span> <span data-ttu-id="87455-106">O assembly não foi carregado e uma exceção <xref:System.IO.FileNotFoundException> ou <xref:System.IO.FileLoadException> é gerada.</span><span class="sxs-lookup"><span data-stu-id="87455-106">The assembly is not loaded and a <xref:System.IO.FileNotFoundException> or <xref:System.IO.FileLoadException> exception is thrown.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="87455-107">Causa</span><span class="sxs-lookup"><span data-stu-id="87455-107">Cause</span></span>  
 <span data-ttu-id="87455-108">Uma falha de associação ocorre quando o tempo de execução não pode carregar um assembly.</span><span class="sxs-lookup"><span data-stu-id="87455-108">A binding failure occurs when the runtime is unable to load an assembly.</span></span> <span data-ttu-id="87455-109">Uma falha de associação pode ser o resultado de uma das seguintes situações:</span><span class="sxs-lookup"><span data-stu-id="87455-109">A binding failure might be the result of one of the following situations:</span></span>  
  
-   <span data-ttu-id="87455-110">O CLR (Common Language Runtime) não pode localizar o assembly solicitado.</span><span class="sxs-lookup"><span data-stu-id="87455-110">The common language runtime (CLR) cannot find the requested assembly.</span></span> <span data-ttu-id="87455-111">Há muitos motivos para que isso ocorra, como o assembly não está sendo instalado ou o aplicativo não está sendo configurado corretamente para localizar o assembly.</span><span class="sxs-lookup"><span data-stu-id="87455-111">There are many reasons this can occur, such as the assembly not being installed or the application not being correctly configured to find the assembly.</span></span>  
  
-   <span data-ttu-id="87455-112">Um cenário comum de problema é a passagem de um tipo para outro domínio do aplicativo, que exige que o CLR carregue o assembly que contém esse tipo no outro domínio do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="87455-112">A common problem scenario is passing a type to another application domain, which requires the CLR to load the assembly containing that type in the other application domain.</span></span> <span data-ttu-id="87455-113">Talvez não seja possível que o tempo de execução carregue o assembly se o domínio do aplicativo estiver configurado de maneira diferente do domínio do aplicativo original.</span><span class="sxs-lookup"><span data-stu-id="87455-113">It may not be possible for the runtime to load the assembly if the other application domain is configured differently from the original application domain.</span></span> <span data-ttu-id="87455-114">Por exemplo, os dois domínios do aplicativo podem ter valores de propriedade <xref:System.AppDomain.BaseDirectory%2A> diferentes.</span><span class="sxs-lookup"><span data-stu-id="87455-114">For example, the two application domains might have different <xref:System.AppDomain.BaseDirectory%2A> property values.</span></span>  
  
-   <span data-ttu-id="87455-115">O assembly solicitado está corrompido ou não é um assembly.</span><span class="sxs-lookup"><span data-stu-id="87455-115">The requested assembly is corrupted or is not an assembly.</span></span>  
  
-   <span data-ttu-id="87455-116">O código que está tentando carregar o assembly não tem as permissões corretas de segurança de acesso do código para carregar assemblies.</span><span class="sxs-lookup"><span data-stu-id="87455-116">The code attempting to load the assembly does not have the correct code access security permissions to load assemblies.</span></span>  
  
-   <span data-ttu-id="87455-117">As credenciais do usuário não fornecem as permissões necessárias para ler o arquivo.</span><span class="sxs-lookup"><span data-stu-id="87455-117">The user credentials do not provide the required permissions to read the file.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="87455-118">Resolução</span><span class="sxs-lookup"><span data-stu-id="87455-118">Resolution</span></span>  
 <span data-ttu-id="87455-119">A primeira etapa é determinar por que o CLR não pôde ser associado ao assembly solicitado.</span><span class="sxs-lookup"><span data-stu-id="87455-119">The first step is to determine why the CLR could not bind to the requested assembly.</span></span> <span data-ttu-id="87455-120">Há muitas razões pelas quais o tempo de execução pode não ter encontrado ou não pôde carregar o assembly solicitado, como os cenários listados na seção Causa.</span><span class="sxs-lookup"><span data-stu-id="87455-120">There are many reasons why the runtime might not have found or been able load the requested assembly, such as the scenarios listed in the Cause section.</span></span> <span data-ttu-id="87455-121">As seguintes ações são recomendadas para eliminar a causa da falha de associação:</span><span class="sxs-lookup"><span data-stu-id="87455-121">The following actions are recommended to eliminate the cause of the binding failure:</span></span>  
  
-   <span data-ttu-id="87455-122">Determine a causa usando os dados fornecidos pelo MDA `bindingFailure`:</span><span class="sxs-lookup"><span data-stu-id="87455-122">Determine the cause by using the data provided by the `bindingFailure` MDA:</span></span>  
  
    -   <span data-ttu-id="87455-123">Execute o [Fuslogvw.exe (Visualizador de Log de Associação do Assembly)](../../../docs/framework/tools/fuslogvw-exe-assembly-binding-log-viewer.md) para ler os logs de erro produzidos pelo associador do assembly.</span><span class="sxs-lookup"><span data-stu-id="87455-123">Run the [Fuslogvw.exe (Assembly Binding Log Viewer)](../../../docs/framework/tools/fuslogvw-exe-assembly-binding-log-viewer.md) to read the error logs produced by the assembly binder.</span></span>  
  
    -   <span data-ttu-id="87455-124">Determine se o assembly está no local solicitado.</span><span class="sxs-lookup"><span data-stu-id="87455-124">Determine if the assembly is at the location requested.</span></span> <span data-ttu-id="87455-125">No caso dos métodos <xref:System.Reflection.Assembly.LoadFrom%2A> e <xref:System.Reflection.Assembly.LoadFile%2A>, o local solicitado pode ser determinado com facilidade.</span><span class="sxs-lookup"><span data-stu-id="87455-125">In the case of the <xref:System.Reflection.Assembly.LoadFrom%2A> and <xref:System.Reflection.Assembly.LoadFile%2A> methods, the requested location can be easily determined.</span></span> <span data-ttu-id="87455-126">No caso do método <xref:System.Reflection.Assembly.Load%2A>, que é associado usando a identidade do assembly, você deve procurar assemblies que correspondem à identidade no caminho de investigação da propriedade <xref:System.AppDomain.BaseDirectory%2A> do domínio do aplicativo e no cache de assembly global.</span><span class="sxs-lookup"><span data-stu-id="87455-126">In the case of the <xref:System.Reflection.Assembly.Load%2A> method, which binds using the assembly identity, you must look for assemblies that match that identity in the application domain's <xref:System.AppDomain.BaseDirectory%2A> property probe path and the global assembly cache.</span></span>  
  
-   <span data-ttu-id="87455-127">Resolva a causa conforme a determinação anterior.</span><span class="sxs-lookup"><span data-stu-id="87455-127">Resolve the cause based on the preceding determination.</span></span> <span data-ttu-id="87455-128">As possíveis opções de resolução são as seguintes:</span><span class="sxs-lookup"><span data-stu-id="87455-128">Possible resolution options are the following:</span></span>  
  
    -   <span data-ttu-id="87455-129">Instale o assembly solicitado no cache de assembly global e chame o</span><span class="sxs-lookup"><span data-stu-id="87455-129">Install the requested assembly in the global assembly cache and call the.</span></span> <span data-ttu-id="87455-130">método <xref:System.Reflection.Assembly.Load%2A> para carregar o assembly por identidade.</span><span class="sxs-lookup"><span data-stu-id="87455-130"><xref:System.Reflection.Assembly.Load%2A> method to load the assembly by identity.</span></span>  
  
    -   <span data-ttu-id="87455-131">Copie o assembly solicitado para o diretório do aplicativo e chame o método <xref:System.Reflection.Assembly.Load%2A> para carregar o assembly por identidade.</span><span class="sxs-lookup"><span data-stu-id="87455-131">Copy the requested assembly into the application directory and call the <xref:System.Reflection.Assembly.Load%2A> method to load the assembly by identity.</span></span>  
  
    -   <span data-ttu-id="87455-132">Reconfigure o domínio do aplicativo no qual ocorreu a falha de associação para incluir o caminho do assembly alterando a propriedade <xref:System.AppDomain.BaseDirectory%2A> ou adicionando caminhos de investigação particulares.</span><span class="sxs-lookup"><span data-stu-id="87455-132">Reconfigure the application domain in which the binding failure occurred to include the assembly path by either changing the <xref:System.AppDomain.BaseDirectory%2A> property or adding private probing paths.</span></span>  
  
    -   <span data-ttu-id="87455-133">Altere a lista de controle de acesso do arquivo para permitir que o usuário conectado leia o arquivo.</span><span class="sxs-lookup"><span data-stu-id="87455-133">Change the access control list for the file to allow the logged-on user to read the file.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="87455-134">Efeito sobre o tempo de execução</span><span class="sxs-lookup"><span data-stu-id="87455-134">Effect on the Runtime</span></span>  
 <span data-ttu-id="87455-135">Esse MDA não tem efeito sobre o CLR.</span><span class="sxs-lookup"><span data-stu-id="87455-135">This MDA has no effect on the CLR.</span></span> <span data-ttu-id="87455-136">Ele relata apenas os dados sobre falhas de associação.</span><span class="sxs-lookup"><span data-stu-id="87455-136">It only reports data about binding failures.</span></span>  
  
## <a name="output"></a><span data-ttu-id="87455-137">Saída</span><span class="sxs-lookup"><span data-stu-id="87455-137">Output</span></span>  
 <span data-ttu-id="87455-138">O MDA relata o assembly que falhou ao ser carregado, incluindo o caminho solicitado e/ou nome de exibição, o contexto de associação, o domínio do aplicativo no qual a carga foi solicitada e o motivo da falha.</span><span class="sxs-lookup"><span data-stu-id="87455-138">The MDA reports the assembly that failed to load, including the requested path and/or display name, the binding context, the application domain in which the load was requested, and the reason for the failure.</span></span>  
  
 <span data-ttu-id="87455-139">O nome de exibição ou o caminho solicitado pode ficar em branco se esses dados não estavam disponíveis para o CLR.</span><span class="sxs-lookup"><span data-stu-id="87455-139">The display name or requested path may be blank if that data was not available to the CLR.</span></span> <span data-ttu-id="87455-140">Se a chamada que falhou era para o método <xref:System.Reflection.Assembly.Load%2A>, é provável que o tempo de execução não pôde determinar o nome de exibição do assembly.</span><span class="sxs-lookup"><span data-stu-id="87455-140">If the call that failed was to the <xref:System.Reflection.Assembly.Load%2A> method, it is likely the runtime could not determine the display name for the assembly.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="87455-141">Configuração</span><span class="sxs-lookup"><span data-stu-id="87455-141">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <bindingFailure />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="example"></a><span data-ttu-id="87455-142">Exemplo</span><span class="sxs-lookup"><span data-stu-id="87455-142">Example</span></span>  
 <span data-ttu-id="87455-143">O seguinte exemplo de código demonstra uma situação que pode ativar esse MDA:</span><span class="sxs-lookup"><span data-stu-id="87455-143">The following code example demonstrates a situation that can activate this MDA:</span></span>  
  
```  
using System;  
using System.Collections.Generic;  
using System.Text;  
using System.Reflection;  
namespace ConsoleApplication1  
{  
    class Program  
    {  
        static void Main(string[] args)  
        {  
            // This call attempts to load a nonexistent assembly.  
            // The call will throw a System.IO.FileNotFound exception  
            // and cause the activation of the bindingFailure MDA   
            // if it is registered.  
            Assembly.Load("NonExistentAssembly");  
        }  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="87455-144">Consulte também</span><span class="sxs-lookup"><span data-stu-id="87455-144">See Also</span></span>  
 [<span data-ttu-id="87455-145">Diagnosticando erros com Assistentes de Depuração Gerenciados</span><span class="sxs-lookup"><span data-stu-id="87455-145">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)

