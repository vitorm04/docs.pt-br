---
title: 'Como: Gerar assemblies de interoperabilidade com base em bibliotecas de tipos'
ms.date: 03/30/2017
helpviewer_keywords:
- importing type library
- interop assemblies, generating
- Type Library Importer
- type libraries
- COM interop, importing type library
ms.assetid: 4afd40c3-68f2-41c5-8ec1-4951bc148b9c
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3a3ee82a9091f0caeee010ec79632ce703efb589
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59338833"
---
# <a name="how-to-generate-interop-assemblies-from-type-libraries"></a><span data-ttu-id="30f38-102">Como: Gerar assemblies de interoperabilidade com base em bibliotecas de tipos</span><span class="sxs-lookup"><span data-stu-id="30f38-102">How to: Generate Interop Assemblies from Type Libraries</span></span>
<span data-ttu-id="30f38-103">O [Importador da Biblioteca de Tipos (Tlbimp.exe)](../../../docs/framework/tools/tlbimp-exe-type-library-importer.md) é uma ferramenta de linha de comando que converte as classes e interfaces contidas em uma biblioteca de tipos COM em metadados.</span><span class="sxs-lookup"><span data-stu-id="30f38-103">The [Type Library Importer (Tlbimp.exe)](../../../docs/framework/tools/tlbimp-exe-type-library-importer.md) is a command-line tool that converts the coclasses and interfaces contained in a COM type library to metadata.</span></span> <span data-ttu-id="30f38-104">Essa ferramenta cria automaticamente um assembly de interoperabilidade e o namespace para as informações de tipo.</span><span class="sxs-lookup"><span data-stu-id="30f38-104">This tool creates an interop assembly and namespace for the type information automatically.</span></span> <span data-ttu-id="30f38-105">Depois que os metadados de uma classe estiverem disponíveis, os clientes gerenciados podem criar instâncias do tipo COM e chamar os métodos dele, como se fosse uma instância do .NET.</span><span class="sxs-lookup"><span data-stu-id="30f38-105">After the metadata of a class is available, managed clients can create instances of the COM type and call its methods, just as if it were a .NET instance.</span></span> <span data-ttu-id="30f38-106">O Tlbimp.exe converte uma biblioteca de tipos inteira em metadados de uma só vez e não é capaz de gerar informações de tipo para um subconjunto dos tipos definidos em uma biblioteca de tipos.</span><span class="sxs-lookup"><span data-stu-id="30f38-106">Tlbimp.exe converts an entire type library to metadata at once and cannot generate type information for a subset of the types defined in a type library.</span></span>  
  
### <a name="to-generate-an-interop-assembly-from-a-type-library"></a><span data-ttu-id="30f38-107">Para gerar um assembly de interoperabilidade de uma biblioteca de tipos</span><span class="sxs-lookup"><span data-stu-id="30f38-107">To generate an interop assembly from a type library</span></span>  
  
1. <span data-ttu-id="30f38-108">Use o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="30f38-108">Use the following command:</span></span>  
  
     <span data-ttu-id="30f38-109">**tlbimp** \<*type-library-file*></span><span class="sxs-lookup"><span data-stu-id="30f38-109">**tlbimp** \<*type-library-file*></span></span>  
  
     <span data-ttu-id="30f38-110">Adicionar a opção **/out:** produz um assembly de interoperabilidade com um nome alterado, como LOANLib.dll.</span><span class="sxs-lookup"><span data-stu-id="30f38-110">Adding the **/out:** switch produces an interop assembly with an altered name, such as LOANLib.dll.</span></span> <span data-ttu-id="30f38-111">A alteração do nome do assembly de interoperabilidade pode ajudar a diferenciá-lo da DLL COM original e evitar problemas que podem ocorrer devido a nomes duplicados.</span><span class="sxs-lookup"><span data-stu-id="30f38-111">Altering the interop assembly name can help distinguish it from the original COM DLL and prevent problems that can occur from having duplicate names.</span></span>  
  
## <a name="example"></a><span data-ttu-id="30f38-112">Exemplo</span><span class="sxs-lookup"><span data-stu-id="30f38-112">Example</span></span>  
 <span data-ttu-id="30f38-113">O comando a seguir produz o assembly Loanlib.dll no namespace `Loanlib`.</span><span class="sxs-lookup"><span data-stu-id="30f38-113">The following command produces the Loanlib.dll assembly in the `Loanlib` namespace.</span></span>  
  
```  
tlbimp Loanlib.tlb  
```  
  
 <span data-ttu-id="30f38-114">O comando a seguir produz um assembly de interoperabilidade com um nome alterado (LOANLib.dll).</span><span class="sxs-lookup"><span data-stu-id="30f38-114">The following command produces an interop assembly with an altered name (LOANLib.dll).</span></span>  
  
```  
tlbimp LoanLib.tlb /out: LOANLib.dll  
```  
  
## <a name="see-also"></a><span data-ttu-id="30f38-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="30f38-115">See also</span></span>

- [<span data-ttu-id="30f38-116">Importando uma biblioteca de tipos como um assembly</span><span class="sxs-lookup"><span data-stu-id="30f38-116">Importing a Type Library as an Assembly</span></span>](../../../docs/framework/interop/importing-a-type-library-as-an-assembly.md)
- [<span data-ttu-id="30f38-117">Expondo componentes do COM ao .NET Framework</span><span class="sxs-lookup"><span data-stu-id="30f38-117">Exposing COM Components to the .NET Framework</span></span>](../../../docs/framework/interop/exposing-com-components.md)
