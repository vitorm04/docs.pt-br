---
title: MDA moduloObjectHashcode
description: Examine o MDA (Assistente de depuração gerenciada) do moduloObjectHashcode, que altera a classe de objeto para obter um valor restante em um resultado de método GetHashCode.
ms.date: 03/30/2017
helpviewer_keywords:
- managed debugging assistants (MDAs), hashcode modulus
- Modulo object hash code
- moduloObjectHashcode MDA
- hashcode modulus
- MDAs (managed debugging assistants), hashcode modulus
- GetHashCode method
- modulus of hashcodes
ms.assetid: b45366ff-2a7a-4b8e-ab01-537b72e9de68
ms.openlocfilehash: a929ec2b9196f1f6cad0528fdf7323839a86fa55
ms.sourcegitcommit: 0edbeb66d71b8df10fcb374cfca4d731b58ccdb2
ms.contentlocale: pt-BR
ms.lasthandoff: 07/07/2020
ms.locfileid: "86052059"
---
# <a name="moduloobjecthashcode-mda"></a><span data-ttu-id="bf714-103">MDA moduloObjectHashcode</span><span class="sxs-lookup"><span data-stu-id="bf714-103">moduloObjectHashcode MDA</span></span>
<span data-ttu-id="bf714-104">O MDA (Assistente de Depuração Gerenciado) de `moduloObjectHashcode` altera o comportamento da classe <xref:System.Object> para executar uma operação de módulo no código hash retornado pelo método <xref:System.Object.GetHashCode%2A>.</span><span class="sxs-lookup"><span data-stu-id="bf714-104">The `moduloObjectHashcode` managed debugging assistant (MDA) changes the behavior of the <xref:System.Object> class to perform a modulo operation on the hash code returned by the <xref:System.Object.GetHashCode%2A> method.</span></span> <span data-ttu-id="bf714-105">O módulo padrão para esse MDA é 1, o que faz com que <xref:System.Object.GetHashCode%2A> retorne 0 para todos os objetos.</span><span class="sxs-lookup"><span data-stu-id="bf714-105">The default modulus for this MDA is 1, which causes <xref:System.Object.GetHashCode%2A> to return 0 for all objects.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="bf714-106">Sintomas</span><span class="sxs-lookup"><span data-stu-id="bf714-106">Symptoms</span></span>  
 <span data-ttu-id="bf714-107">Depois de migrar para uma nova versão do CLR (Common Language Runtime), um programa não é mais executado corretamente:</span><span class="sxs-lookup"><span data-stu-id="bf714-107">After moving to a new version of the common language runtime (CLR), a program no longer executes properly:</span></span>  
  
- <span data-ttu-id="bf714-108">O programa está obtendo o objeto errado de um <xref:System.Collections.Hashtable>.</span><span class="sxs-lookup"><span data-stu-id="bf714-108">The program is getting the wrong object from a <xref:System.Collections.Hashtable>.</span></span>  
  
- <span data-ttu-id="bf714-109">A ordem de enumeração de um <xref:System.Collections.Hashtable> tem uma alteração que interrompe o programa.</span><span class="sxs-lookup"><span data-stu-id="bf714-109">The order of enumeration from a <xref:System.Collections.Hashtable> has a change that breaks the program.</span></span>  
  
- <span data-ttu-id="bf714-110">Dois objetos que costumavam ser iguais não o são mais.</span><span class="sxs-lookup"><span data-stu-id="bf714-110">Two objects that used to be equal are no longer equal.</span></span>  
  
- <span data-ttu-id="bf714-111">Dois objetos que costumavam não ser iguais agora o são.</span><span class="sxs-lookup"><span data-stu-id="bf714-111">Two objects that used to not be equal are now equal.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="bf714-112">Causa</span><span class="sxs-lookup"><span data-stu-id="bf714-112">Cause</span></span>  
 <span data-ttu-id="bf714-113">Seu programa pode estar obtendo o objeto errado de um <xref:System.Collections.Hashtable> porque a implementação do método <xref:System.Object.Equals%2A> na classe para a chave no <xref:System.Collections.Hashtable> testa a igualdade de objetos ao comparar os resultados da chamada para o método <xref:System.Object.GetHashCode%2A>.</span><span class="sxs-lookup"><span data-stu-id="bf714-113">Your program may be getting the wrong object from a <xref:System.Collections.Hashtable> because the implementation of the <xref:System.Object.Equals%2A> method on the class for the key into the <xref:System.Collections.Hashtable> tests for equality of objects by comparing the results of the call to the <xref:System.Object.GetHashCode%2A> method.</span></span> <span data-ttu-id="bf714-114">Códigos hash não devem ser usados para testar a igualdade de objetos porque os dois objetos podem ter o mesmo código hash, mesmo que seus respectivos campos tenham valores diferentes.</span><span class="sxs-lookup"><span data-stu-id="bf714-114">Hash codes should not be used to test for object equality because two objects may have the same hash code even if their respective fields have different values.</span></span> <span data-ttu-id="bf714-115">Esses conflitos de código hash, embora raros na prática, ocorrem.</span><span class="sxs-lookup"><span data-stu-id="bf714-115">These hash code collisions, although rare in practice, do occur.</span></span> <span data-ttu-id="bf714-116">O efeito disso em uma pesquisa <xref:System.Collections.Hashtable> é que duas chaves que não são iguais parecem ser e o objeto errado é retornado do <xref:System.Collections.Hashtable>.</span><span class="sxs-lookup"><span data-stu-id="bf714-116">The effect this has on a <xref:System.Collections.Hashtable> lookup is that two keys which are not equal appear to be equal, and the wrong object is returned from the <xref:System.Collections.Hashtable>.</span></span> <span data-ttu-id="bf714-117">Por motivos de desempenho, a implementação de <xref:System.Object.GetHashCode%2A> pode variar entre as versões de runtime, então colisões que podem não ocorrer em uma versão podem ocorrer em versões subsequentes.</span><span class="sxs-lookup"><span data-stu-id="bf714-117">For performance reasons, the implementation of <xref:System.Object.GetHashCode%2A> can change between runtime versions, so collisions that might not occur on one version might occur on subsequent versions.</span></span> <span data-ttu-id="bf714-118">Quando códigos hash entrarem em conflito, habilite esse MDA para testar se o seu código tem bugs.</span><span class="sxs-lookup"><span data-stu-id="bf714-118">Enable this MDA to test whether your code has bugs when hash codes collide.</span></span> <span data-ttu-id="bf714-119">Quando habilitado, esse MDA faz com que o método <xref:System.Object.GetHashCode%2A> retorne 0, resultando em uma colisão de todos os códigos hash.</span><span class="sxs-lookup"><span data-stu-id="bf714-119">When enabled, this MDA causes the <xref:System.Object.GetHashCode%2A> method to return 0, resulting in all hash codes colliding.</span></span> <span data-ttu-id="bf714-120">O único efeito que habilitar esse MDA deve ter em seu programa é tornar a execução dele mais lenta.</span><span class="sxs-lookup"><span data-stu-id="bf714-120">The only effect enabling this MDA should have on your program is that your program runs slower.</span></span>  
  
 <span data-ttu-id="bf714-121">A ordem de enumeração de um <xref:System.Collections.Hashtable> poderá variar de uma versão de runtime para outra se o algoritmo usado para calcular os códigos hash para a chave for alterado.</span><span class="sxs-lookup"><span data-stu-id="bf714-121">The order of enumeration from a <xref:System.Collections.Hashtable> may change from one version of the runtime to another if the algorithm used to compute the hash codes for the key change.</span></span> <span data-ttu-id="bf714-122">Para testar se o seu programa obteve uma dependência na ordem de enumeração de chaves ou valores de uma tabela de hash, você pode habilitar esse MDA.</span><span class="sxs-lookup"><span data-stu-id="bf714-122">To test whether your program has taken a dependency on the order of enumeration of keys or values out of a hash table, you can enable this MDA.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="bf714-123">Resolução</span><span class="sxs-lookup"><span data-stu-id="bf714-123">Resolution</span></span>  
 <span data-ttu-id="bf714-124">Nunca use códigos hash como um substituto para a identidade do objeto.</span><span class="sxs-lookup"><span data-stu-id="bf714-124">Never use hash codes as a substitute for object identity.</span></span> <span data-ttu-id="bf714-125">Implemente a substituição do método <xref:System.Object.Equals%2A?displayProperty=nameWithType> para não comparar códigos hash.</span><span class="sxs-lookup"><span data-stu-id="bf714-125">Implement the override of the <xref:System.Object.Equals%2A?displayProperty=nameWithType> method to not compare hash codes.</span></span>  
  
 <span data-ttu-id="bf714-126">Não crie dependências na ordem das enumerações de chaves ou valores em tabelas de hash.</span><span class="sxs-lookup"><span data-stu-id="bf714-126">Do not create dependencies on the order of enumerations of keys or values in hash tables.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="bf714-127">Efeito sobre o runtime</span><span class="sxs-lookup"><span data-stu-id="bf714-127">Effect on the Runtime</span></span>  
 <span data-ttu-id="bf714-128">Os aplicativos são executados mais lentamente quando esse MDA está habilitado.</span><span class="sxs-lookup"><span data-stu-id="bf714-128">Applications run more slowly when this MDA is enabled.</span></span> <span data-ttu-id="bf714-129">Esse MDA simplesmente usa o código hash que teria sido retornado e em vez disso, retorna o resto quando dividido por um módulo.</span><span class="sxs-lookup"><span data-stu-id="bf714-129">This MDA simply takes the hash code that would have been returned and instead returns the remainder when divided by a modulus.</span></span>  
  
## <a name="output"></a><span data-ttu-id="bf714-130">Saída</span><span class="sxs-lookup"><span data-stu-id="bf714-130">Output</span></span>  
 <span data-ttu-id="bf714-131">Não há nenhuma saída para esse MDA.</span><span class="sxs-lookup"><span data-stu-id="bf714-131">There is no output for this MDA.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="bf714-132">Configuração</span><span class="sxs-lookup"><span data-stu-id="bf714-132">Configuration</span></span>  
 <span data-ttu-id="bf714-133">O atributo `modulus` especifica o módulo usado no código hash.</span><span class="sxs-lookup"><span data-stu-id="bf714-133">The `modulus` attribute specifies the modulus used on the hash code.</span></span> <span data-ttu-id="bf714-134">O valor padrão é 1.</span><span class="sxs-lookup"><span data-stu-id="bf714-134">The default value is 1.</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <moduloObjectHashcode modulus="1" />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="bf714-135">Consulte também</span><span class="sxs-lookup"><span data-stu-id="bf714-135">See also</span></span>

- <xref:System.Object.GetHashCode%2A?displayProperty=nameWithType>
- <xref:System.Object.Equals%2A?displayProperty=nameWithType>
- [<span data-ttu-id="bf714-136">Diagnosticando erros com assistentes para depuração gerenciada</span><span class="sxs-lookup"><span data-stu-id="bf714-136">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
