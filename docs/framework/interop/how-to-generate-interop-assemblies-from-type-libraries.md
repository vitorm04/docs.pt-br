---
title: 'Como: Gerar assemblies de interoperabilidade com base em bibliotecas de tipos'
description: Gere assemblies de interoperabilidade de bibliotecas de tipos. Use o importador da biblioteca de tipos (Tlbimp.exe) para converter coclasses e interfaces de uma biblioteca de tipos COM em metadados.
ms.date: 03/30/2017
helpviewer_keywords:
- importing type library
- interop assemblies, generating
- Type Library Importer
- type libraries
- COM interop, importing type library
ms.assetid: 4afd40c3-68f2-41c5-8ec1-4951bc148b9c
ms.openlocfilehash: 6f54875d6aadb1da18cf25a1bec0a0e451f4a24c
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619553"
---
# <a name="how-to-generate-interop-assemblies-from-type-libraries"></a><span data-ttu-id="92e84-104">Como: Gerar assemblies de interoperabilidade com base em bibliotecas de tipos</span><span class="sxs-lookup"><span data-stu-id="92e84-104">How to: Generate Interop Assemblies from Type Libraries</span></span>
<span data-ttu-id="92e84-105">O [Importador da Biblioteca de Tipos (Tlbimp.exe)](../tools/tlbimp-exe-type-library-importer.md) é uma ferramenta de linha de comando que converte as classes e interfaces contidas em uma biblioteca de tipos COM em metadados.</span><span class="sxs-lookup"><span data-stu-id="92e84-105">The [Type Library Importer (Tlbimp.exe)](../tools/tlbimp-exe-type-library-importer.md) is a command-line tool that converts the coclasses and interfaces contained in a COM type library to metadata.</span></span> <span data-ttu-id="92e84-106">Essa ferramenta cria automaticamente um assembly de interoperabilidade e o namespace para as informações de tipo.</span><span class="sxs-lookup"><span data-stu-id="92e84-106">This tool creates an interop assembly and namespace for the type information automatically.</span></span> <span data-ttu-id="92e84-107">Depois que os metadados de uma classe estiverem disponíveis, os clientes gerenciados podem criar instâncias do tipo COM e chamar os métodos dele, como se fosse uma instância do .NET.</span><span class="sxs-lookup"><span data-stu-id="92e84-107">After the metadata of a class is available, managed clients can create instances of the COM type and call its methods, just as if it were a .NET instance.</span></span> <span data-ttu-id="92e84-108">O Tlbimp.exe converte uma biblioteca de tipos inteira em metadados de uma só vez e não é capaz de gerar informações de tipo para um subconjunto dos tipos definidos em uma biblioteca de tipos.</span><span class="sxs-lookup"><span data-stu-id="92e84-108">Tlbimp.exe converts an entire type library to metadata at once and cannot generate type information for a subset of the types defined in a type library.</span></span>  
  
### <a name="to-generate-an-interop-assembly-from-a-type-library"></a><span data-ttu-id="92e84-109">Para gerar um assembly de interoperabilidade de uma biblioteca de tipos</span><span class="sxs-lookup"><span data-stu-id="92e84-109">To generate an interop assembly from a type library</span></span>  
  
1. <span data-ttu-id="92e84-110">Use o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="92e84-110">Use the following command:</span></span>  
  
     <span data-ttu-id="92e84-111">**Tlbimp**\<*type-library-file*></span><span class="sxs-lookup"><span data-stu-id="92e84-111">**tlbimp** \<*type-library-file*></span></span>  
  
     <span data-ttu-id="92e84-112">Adicionar a opção **/out:** produz um assembly de interoperabilidade com um nome alterado, como LOANLib.dll.</span><span class="sxs-lookup"><span data-stu-id="92e84-112">Adding the **/out:** switch produces an interop assembly with an altered name, such as LOANLib.dll.</span></span> <span data-ttu-id="92e84-113">A alteração do nome do assembly de interoperabilidade pode ajudar a diferenciá-lo da DLL COM original e evitar problemas que podem ocorrer devido a nomes duplicados.</span><span class="sxs-lookup"><span data-stu-id="92e84-113">Altering the interop assembly name can help distinguish it from the original COM DLL and prevent problems that can occur from having duplicate names.</span></span>  
  
## <a name="example"></a><span data-ttu-id="92e84-114">Exemplo</span><span class="sxs-lookup"><span data-stu-id="92e84-114">Example</span></span>  
 <span data-ttu-id="92e84-115">O comando a seguir produz o assembly Loanlib.dll no namespace `Loanlib`.</span><span class="sxs-lookup"><span data-stu-id="92e84-115">The following command produces the Loanlib.dll assembly in the `Loanlib` namespace.</span></span>  
  
```console  
tlbimp Loanlib.tlb  
```  
  
 <span data-ttu-id="92e84-116">O comando a seguir produz um assembly de interoperabilidade com um nome alterado (LOANLib.dll).</span><span class="sxs-lookup"><span data-stu-id="92e84-116">The following command produces an interop assembly with an altered name (LOANLib.dll).</span></span>  
  
```console  
tlbimp LoanLib.tlb /out: LOANLib.dll  
```  
  
## <a name="see-also"></a><span data-ttu-id="92e84-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="92e84-117">See also</span></span>

- [<span data-ttu-id="92e84-118">Importando uma biblioteca de tipos como um assembly</span><span class="sxs-lookup"><span data-stu-id="92e84-118">Importing a Type Library as an Assembly</span></span>](importing-a-type-library-as-an-assembly.md)
- [<span data-ttu-id="92e84-119">Expondo componentes do COM para o .NET Framework</span><span class="sxs-lookup"><span data-stu-id="92e84-119">Exposing COM Components to the .NET Framework</span></span>](exposing-com-components.md)
