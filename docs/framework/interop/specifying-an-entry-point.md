---
title: Especificando um ponto de entrada
ms.date: 03/30/2017
helpviewer_keywords:
- EntryPoint field
- platform invoke, attribute fields
- attribute fields in platform invoke, EntryPoint
ms.assetid: d1247f08-0965-416a-b978-e0b50652dfe3
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c278eca421020bea4f36f87eb6c8a9a8ba7d2a43
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54658280"
---
# <a name="specifying-an-entry-point"></a><span data-ttu-id="22f48-102">Especificando um ponto de entrada</span><span class="sxs-lookup"><span data-stu-id="22f48-102">Specifying an Entry Point</span></span>
<span data-ttu-id="22f48-103">Um ponto de entrada identifica o local de uma função em uma DLL.</span><span class="sxs-lookup"><span data-stu-id="22f48-103">An entry point identifies the location of a function in a DLL.</span></span> <span data-ttu-id="22f48-104">Em um projeto gerenciado, o nome original ou o ponto de entrada ordinal de uma função de destino identifica essa função no limite de interoperação.</span><span class="sxs-lookup"><span data-stu-id="22f48-104">Within a managed project, the original name or ordinal entry point of a target function identifies that function across the interoperation boundary.</span></span> <span data-ttu-id="22f48-105">Além disso, é possível mapear o ponto de entrada para um nome diferente, renomeando a função efetivamente.</span><span class="sxs-lookup"><span data-stu-id="22f48-105">Further, you can map the entry point to a different name, effectively renaming the function.</span></span>  
  
 <span data-ttu-id="22f48-106">Veja a seguir uma lista dos possíveis motivos para renomear uma função de DLL:</span><span class="sxs-lookup"><span data-stu-id="22f48-106">Following is a list of possible reasons to rename a DLL function:</span></span>  
  
-   <span data-ttu-id="22f48-107">Para evitar o uso de nomes de função de API que diferenciam maiúsculas de minúsculas</span><span class="sxs-lookup"><span data-stu-id="22f48-107">To avoid using case-sensitive API function names</span></span>  
  
-   <span data-ttu-id="22f48-108">Para estar em conformidade com os padrões de nomenclatura existentes</span><span class="sxs-lookup"><span data-stu-id="22f48-108">To comply with existing naming standards</span></span>  
  
-   <span data-ttu-id="22f48-109">Para acomodar funções que usam tipos de dados diferentes (declarando várias versões da mesma função de DLL)</span><span class="sxs-lookup"><span data-stu-id="22f48-109">To accommodate functions that take different data types (by declaring multiple versions of the same DLL function)</span></span>  
  
-   <span data-ttu-id="22f48-110">Para simplificar o uso de APIs que contêm versões ANSI e Unicode</span><span class="sxs-lookup"><span data-stu-id="22f48-110">To simplify using APIs that contain ANSI and Unicode versions</span></span>  
  
 <span data-ttu-id="22f48-111">Este tópico demonstra como renomear uma função de DLL em um código gerenciado.</span><span class="sxs-lookup"><span data-stu-id="22f48-111">This topic demonstrates how to rename a DLL function in managed code.</span></span>  
  
## <a name="renaming-a-function-in-visual-basic"></a><span data-ttu-id="22f48-112">Renomeando uma função no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="22f48-112">Renaming a Function in Visual Basic</span></span>  
 <span data-ttu-id="22f48-113">O Visual Basic usa a palavra-chave **Function** na instrução **Declare** para definir o campo <xref:System.Runtime.InteropServices.DllImportAttribute.EntryPoint?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="22f48-113">Visual Basic uses the **Function** keyword in the **Declare** statement to set the <xref:System.Runtime.InteropServices.DllImportAttribute.EntryPoint?displayProperty=nameWithType> field.</span></span> <span data-ttu-id="22f48-114">O exemplo a seguir mostra uma declaração básica.</span><span class="sxs-lookup"><span data-stu-id="22f48-114">The following example shows a basic declaration.</span></span>  
  
```vb  
Imports System.Runtime.InteropServices  
  
Public Class Win32  
    Declare Auto Function MessageBox Lib "user32.dll" _  
       (ByVal hWnd As Integer, ByVal txt As String,_  
       ByVal caption As String, ByVal Typ As Integer) As Integer  
End Class  
```  
  
 <span data-ttu-id="22f48-115">É possível substituir o ponto de entrada **MessageBox** por **MsgBox** incluindo a palavra-chave **Alias** na definição, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="22f48-115">You can replace the **MessageBox** entry point with **MsgBox** by including the **Alias** keyword in your definition, as shown in the following example.</span></span> <span data-ttu-id="22f48-116">Nos dois exemplos, a palavra-chave **Auto** elimina a necessidade de especificar a versão do conjunto de caracteres do ponto de entrada.</span><span class="sxs-lookup"><span data-stu-id="22f48-116">In both examples the **Auto** keyword eliminates the need to specify the character-set version of the entry point.</span></span> <span data-ttu-id="22f48-117">Para obter mais informações sobre como selecionar um conjunto de caracteres, consulte [Especificando um conjunto de caracteres](../../../docs/framework/interop/specifying-a-character-set.md).</span><span class="sxs-lookup"><span data-stu-id="22f48-117">For more information about selecting a character set, see [Specifying a Character Set](../../../docs/framework/interop/specifying-a-character-set.md).</span></span>  
  
```vb  
Imports System.Runtime.InteropServices  
  
Public Class Win32  
    Declare Auto Function MsgBox Lib "user32.dll" _  
       Alias "MessageBox" (ByVal hWnd As Integer, ByVal txt As String,_  
       ByVal caption As String, ByVal Typ As Integer) As Integer  
End Class  
```  
  
## <a name="renaming-a-function-in-c-and-c"></a><span data-ttu-id="22f48-118">Renomeando uma função no C# e C++</span><span class="sxs-lookup"><span data-stu-id="22f48-118">Renaming a Function in C# and C++</span></span>  
 <span data-ttu-id="22f48-119">É possível usar o campo <xref:System.Runtime.InteropServices.DllImportAttribute.EntryPoint?displayProperty=nameWithType> para especificar uma função de DLL por nome ou ordinal.</span><span class="sxs-lookup"><span data-stu-id="22f48-119">You can use the <xref:System.Runtime.InteropServices.DllImportAttribute.EntryPoint?displayProperty=nameWithType> field to specify a DLL function by name or ordinal.</span></span> <span data-ttu-id="22f48-120">Se o nome da função na definição de método for o mesmo do ponto de entrada na DLL, você não precisará identificar explicitamente a função com o campo **EntryPoint**.</span><span class="sxs-lookup"><span data-stu-id="22f48-120">If the name of the function in your method definition is the same as the entry point in the DLL, you do not have to explicitly identify the function with the **EntryPoint** field.</span></span> <span data-ttu-id="22f48-121">Caso contrário, use um dos seguintes formatos de atributo para indicar um nome ou um ordinal:</span><span class="sxs-lookup"><span data-stu-id="22f48-121">Otherwise, use one of the following attribute forms to indicate a name or ordinal:</span></span>  
  
```  
[DllImport("dllname", EntryPoint="Functionname")]  
[DllImport("dllname", EntryPoint="#123")]  
```  
  
 <span data-ttu-id="22f48-122">Observe que é necessário prefixar um ordinal com o sinal de cerquilha (#).</span><span class="sxs-lookup"><span data-stu-id="22f48-122">Notice that you must prefix an ordinal with the pound sign (#).</span></span>  
  
 <span data-ttu-id="22f48-123">O exemplo a seguir demonstra como substituir **MessageBoxA** por **MsgBox** no código usando o campo **EntryPoint**.</span><span class="sxs-lookup"><span data-stu-id="22f48-123">The following example demonstrates how to replace **MessageBoxA** with **MsgBox** in your code by using the **EntryPoint** field.</span></span>  
  
```csharp  
using System.Runtime.InteropServices;  
  
public class Win32 {  
    [DllImport("user32.dll", EntryPoint="MessageBoxA")]  
    public static extern int MsgBox(int hWnd, String text, String caption,  
                                    uint type);  
}  
```  
  
```cpp  
using namespace System::Runtime::InteropServices;  
  
typedef void* HWND;  
[DllImport("user32", EntryPoint="MessageBoxA")]  
extern "C" int MsgBox(HWND hWnd,  
                      String*  pText,  
                      String*  pCaption,  
                      unsigned int uType);  
```  
  
## <a name="see-also"></a><span data-ttu-id="22f48-124">Consulte também</span><span class="sxs-lookup"><span data-stu-id="22f48-124">See also</span></span>
- <xref:System.Runtime.InteropServices.DllImportAttribute>
- [<span data-ttu-id="22f48-125">Criando protótipos em código gerenciado</span><span class="sxs-lookup"><span data-stu-id="22f48-125">Creating Prototypes in Managed Code</span></span>](../../../docs/framework/interop/creating-prototypes-in-managed-code.md)
- [<span data-ttu-id="22f48-126">Exemplos de invocação de plataforma</span><span class="sxs-lookup"><span data-stu-id="22f48-126">Platform Invoke Examples</span></span>](../../../docs/framework/interop/platform-invoke-examples.md)
- [<span data-ttu-id="22f48-127">Marshaling de dados com a invocação de plataforma</span><span class="sxs-lookup"><span data-stu-id="22f48-127">Marshaling Data with Platform Invoke</span></span>](../../../docs/framework/interop/marshaling-data-with-platform-invoke.md)
