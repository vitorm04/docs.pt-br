---
title: "Marshaling padrão para matrizes"
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
- interop marshaling, arrays
- arrays, interop marshaling
ms.assetid: 8a3cca8b-dd94-4e3d-ad9a-9ee7590654bc
caps.latest.revision: 19
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 72b9cf51936df7b3b2055823ff33f7561640608f
ms.contentlocale: pt-br
ms.lasthandoff: 08/21/2017

---
# <a name="default-marshaling-for-arrays"></a><span data-ttu-id="bc418-102">Marshaling padrão para matrizes</span><span class="sxs-lookup"><span data-stu-id="bc418-102">Default Marshaling for Arrays</span></span>
<span data-ttu-id="bc418-103">Em um aplicativo que consiste inteiramente em um código gerenciado, o Common Language Runtime passa tipos de matriz como parâmetros de Entrada/Saída.</span><span class="sxs-lookup"><span data-stu-id="bc418-103">In an application consisting entirely of managed code, the common language runtime passes array types as In/Out parameters.</span></span> <span data-ttu-id="bc418-104">Por outro lado, o marshaler de interoperabilidade passa uma matriz como parâmetros de Entrada, por padrão.</span><span class="sxs-lookup"><span data-stu-id="bc418-104">In contrast, the interop marshaler passes an array as In parameters by default.</span></span>  
  
 <span data-ttu-id="bc418-105">Com a [otimização de anexação](../../../docs/framework/interop/copying-and-pinning.md), uma matriz blittable pode aparecer operar como um parâmetro de Entrada/Saída ao interagir com objetos no mesmo apartment.</span><span class="sxs-lookup"><span data-stu-id="bc418-105">With [pinning optimization](../../../docs/framework/interop/copying-and-pinning.md), a blittable array can appear to operate as an In/Out parameter when interacting with objects in the same apartment.</span></span> <span data-ttu-id="bc418-106">No entanto, se você exportar o código posteriormente para uma biblioteca de tipos usada para gerar o proxy entre computadores e essa biblioteca for usada para realizar marshaling das chamadas entre apartments, as chamadas poderão reverter como verdadeiro o comportamento do parâmetro de Entrada.</span><span class="sxs-lookup"><span data-stu-id="bc418-106">However, if you later export the code to a type library used to generate the cross-machine proxy, and that library is used to marshal your calls across apartments, the calls can revert to true In parameter behavior.</span></span>  
  
 <span data-ttu-id="bc418-107">Matrizes são complexas por natureza e as distinções entre matrizes gerenciadas e não gerenciadas garantem mais informações do que outros tipos não blittable.</span><span class="sxs-lookup"><span data-stu-id="bc418-107">Arrays are complex by nature, and the distinctions between managed and unmanaged arrays warrant more information than other non-blittable types.</span></span> <span data-ttu-id="bc418-108">Este tópico fornece as seguintes informações sobre o marshaling de matrizes:</span><span class="sxs-lookup"><span data-stu-id="bc418-108">This topic provides the following information on marshaling arrays:</span></span>  
  
-   [<span data-ttu-id="bc418-109">Matrizes gerenciadas</span><span class="sxs-lookup"><span data-stu-id="bc418-109">Managed Arrays</span></span>](#cpcondefaultmarshalingforarraysanchor1)  
  
-   [<span data-ttu-id="bc418-110">Matrizes não gerenciadas</span><span class="sxs-lookup"><span data-stu-id="bc418-110">Unmanaged Arrays</span></span>](#cpcondefaultmarshalingforarraysanchor2)  
  
-   [<span data-ttu-id="bc418-111">Passando parâmetros de matriz para um código do .NET</span><span class="sxs-lookup"><span data-stu-id="bc418-111">Passing Array Parameters to .NET Code</span></span>](#cpcondefaultmarshalingforarraysanchor3)  
  
-   [<span data-ttu-id="bc418-112">Passando matrizes para o COM</span><span class="sxs-lookup"><span data-stu-id="bc418-112">Passing Arrays to COM</span></span>](#cpcondefaultmarshalingforarraysanchor4)  
  
<a name="cpcondefaultmarshalingforarraysanchor1"></a>   
## <a name="managed-arrays"></a><span data-ttu-id="bc418-113">Matrizes gerenciadas</span><span class="sxs-lookup"><span data-stu-id="bc418-113">Managed Arrays</span></span>  
 <span data-ttu-id="bc418-114">Os tipos de matriz gerenciada podem variar; no entanto, a classe <xref:System.Array?displayProperty=fullName> é a classe base de todos os tipos de matriz.</span><span class="sxs-lookup"><span data-stu-id="bc418-114">Managed array types can vary; however, the <xref:System.Array?displayProperty=fullName> class is the base class of all array types.</span></span> <span data-ttu-id="bc418-115">A classe **System.Array** tem propriedades para determinar a classificação, o tamanho e os limites inferior e superior de uma matriz, bem como métodos para acessar, classificar, pesquisar, copiar e criar matrizes.</span><span class="sxs-lookup"><span data-stu-id="bc418-115">The **System.Array** class has properties for determining the rank, length, and lower and upper bounds of an array, as well as methods for accessing, sorting, searching, copying, and creating arrays.</span></span>  
  
 <span data-ttu-id="bc418-116">Esses tipos de matriz são dinâmicos e não tem um tipo estático correspondente definido na biblioteca de classes base.</span><span class="sxs-lookup"><span data-stu-id="bc418-116">These array types are dynamic and do not have a corresponding static type defined in the base class library.</span></span> <span data-ttu-id="bc418-117">É conveniente pensar em cada combinação de tipo de elemento e classificação como um tipo distinto de matriz.</span><span class="sxs-lookup"><span data-stu-id="bc418-117">It is convenient to think of each combination of element type and rank as a distinct type of array.</span></span> <span data-ttu-id="bc418-118">Portanto, uma matriz unidimensional de inteiros é de um tipo diferente do que uma matriz unidimensional de tipos double.</span><span class="sxs-lookup"><span data-stu-id="bc418-118">Therefore, a one-dimensional array of integers is of a different type than a one-dimensional array of double types.</span></span> <span data-ttu-id="bc418-119">Da mesma forma, uma matriz bidimensional de inteiros é diferente de uma matriz unidimensional de inteiros.</span><span class="sxs-lookup"><span data-stu-id="bc418-119">Similarly a two-dimensional array of integers is different from a one-dimensional array of integers.</span></span> <span data-ttu-id="bc418-120">Os limites da matriz não são considerados durante a comparação de tipos.</span><span class="sxs-lookup"><span data-stu-id="bc418-120">The bounds of the array are not considered when comparing types.</span></span>  
  
 <span data-ttu-id="bc418-121">Como mostra a tabela a seguir, qualquer instância de uma matriz gerenciada deve ser de um tipo de elemento, classificação e limite inferior específicos.</span><span class="sxs-lookup"><span data-stu-id="bc418-121">As the following table shows, any instance of a managed array must be of a specific element type, rank, and lower bound.</span></span>  
  
|<span data-ttu-id="bc418-122">Tipo de matriz gerenciada</span><span class="sxs-lookup"><span data-stu-id="bc418-122">Managed array type</span></span>|<span data-ttu-id="bc418-123">Tipo de elemento</span><span class="sxs-lookup"><span data-stu-id="bc418-123">Element type</span></span>|<span data-ttu-id="bc418-124">Classificação</span><span class="sxs-lookup"><span data-stu-id="bc418-124">Rank</span></span>|<span data-ttu-id="bc418-125">Limite inferior</span><span class="sxs-lookup"><span data-stu-id="bc418-125">Lower bound</span></span>|<span data-ttu-id="bc418-126">Notação de assinatura</span><span class="sxs-lookup"><span data-stu-id="bc418-126">Signature notation</span></span>|  
|------------------------|------------------|----------|-----------------|------------------------|  
|<span data-ttu-id="bc418-127">**ELEMENT_TYPE_ARRAY**</span><span class="sxs-lookup"><span data-stu-id="bc418-127">**ELEMENT_TYPE_ARRAY**</span></span>|<span data-ttu-id="bc418-128">Especificado pelo tipo.</span><span class="sxs-lookup"><span data-stu-id="bc418-128">Specified by type.</span></span>|<span data-ttu-id="bc418-129">Especificado pela classificação.</span><span class="sxs-lookup"><span data-stu-id="bc418-129">Specified by rank.</span></span>|<span data-ttu-id="bc418-130">Opcionalmente, especificado pelos limites.</span><span class="sxs-lookup"><span data-stu-id="bc418-130">Optionally specified by bounds.</span></span>|<span data-ttu-id="bc418-131">*type* **[** *n*,*m* **]**</span><span class="sxs-lookup"><span data-stu-id="bc418-131">*type* **[** *n*,*m* **]**</span></span>|  
|<span data-ttu-id="bc418-132">**ELEMENT_TYPE_CLASS**</span><span class="sxs-lookup"><span data-stu-id="bc418-132">**ELEMENT_TYPE_CLASS**</span></span>|<span data-ttu-id="bc418-133">Unknown</span><span class="sxs-lookup"><span data-stu-id="bc418-133">Unknown</span></span>|<span data-ttu-id="bc418-134">Unknown</span><span class="sxs-lookup"><span data-stu-id="bc418-134">Unknown</span></span>|<span data-ttu-id="bc418-135">Unknown</span><span class="sxs-lookup"><span data-stu-id="bc418-135">Unknown</span></span>|<span data-ttu-id="bc418-136">**System.Array**</span><span class="sxs-lookup"><span data-stu-id="bc418-136">**System.Array**</span></span>|  
|<span data-ttu-id="bc418-137">**ELEMENT_TYPE_SZARRAY**</span><span class="sxs-lookup"><span data-stu-id="bc418-137">**ELEMENT_TYPE_SZARRAY**</span></span>|<span data-ttu-id="bc418-138">Especificado pelo tipo.</span><span class="sxs-lookup"><span data-stu-id="bc418-138">Specified by type.</span></span>|<span data-ttu-id="bc418-139">1</span><span class="sxs-lookup"><span data-stu-id="bc418-139">1</span></span>|<span data-ttu-id="bc418-140">0</span><span class="sxs-lookup"><span data-stu-id="bc418-140">0</span></span>|<span data-ttu-id="bc418-141">*type* **[** *n* **]**</span><span class="sxs-lookup"><span data-stu-id="bc418-141">*type* **[** *n* **]**</span></span>|  
  
<a name="cpcondefaultmarshalingforarraysanchor2"></a>   
## <a name="unmanaged-arrays"></a><span data-ttu-id="bc418-142">Matrizes não gerenciadas</span><span class="sxs-lookup"><span data-stu-id="bc418-142">Unmanaged Arrays</span></span>  
 <span data-ttu-id="bc418-143">Matrizes não gerenciadas são matrizes seguras de estilo COM ou matrizes C-style com comprimento fixo ou variável.</span><span class="sxs-lookup"><span data-stu-id="bc418-143">Unmanaged arrays are either COM-style safe arrays or C-style arrays with fixed or variable length.</span></span> <span data-ttu-id="bc418-144">Matrizes seguras são matrizes autodescritivas que levam o tipo, a classificação e os limites dos dados da matriz associada.</span><span class="sxs-lookup"><span data-stu-id="bc418-144">Safe arrays are self-describing arrays that carry the type, rank, and bounds of the associated array data.</span></span> <span data-ttu-id="bc418-145">Matrizes C-style são matrizes tipadas unidimensionais com um limite inferior fixo igual a 0.</span><span class="sxs-lookup"><span data-stu-id="bc418-145">C-style arrays are one-dimensional typed arrays with a fixed lower bound of 0.</span></span> <span data-ttu-id="bc418-146">O serviço de marshaling tem suporte limitado para ambos os tipos de matrizes.</span><span class="sxs-lookup"><span data-stu-id="bc418-146">The marshaling service has limited support for both types of arrays.</span></span>  
  
<a name="cpcondefaultmarshalingforarraysanchor3"></a>   
## <a name="passing-array-parameters-to-net-code"></a><span data-ttu-id="bc418-147">Passando parâmetros de matriz para um código do .NET</span><span class="sxs-lookup"><span data-stu-id="bc418-147">Passing Array Parameters to .NET Code</span></span>  
 <span data-ttu-id="bc418-148">As matrizes C-style e as matrizes seguras podem ser passadas para um código do .NET de um código não gerenciado, como uma matriz segura ou uma matriz C-style.</span><span class="sxs-lookup"><span data-stu-id="bc418-148">Both C-style arrays and safe arrays can be passed to .NET code from unmanaged code as either a safe array or a C-style array.</span></span> <span data-ttu-id="bc418-149">A tabela a seguir mostra o valor de tipo não gerenciado e o tipo importado.</span><span class="sxs-lookup"><span data-stu-id="bc418-149">The following table shows the unmanaged type value and the imported type.</span></span>  
  
|<span data-ttu-id="bc418-150">Tipo não gerenciado</span><span class="sxs-lookup"><span data-stu-id="bc418-150">Unmanaged type</span></span>|<span data-ttu-id="bc418-151">Tipo importado</span><span class="sxs-lookup"><span data-stu-id="bc418-151">Imported type</span></span>|  
|--------------------|-------------------|  
|<span data-ttu-id="bc418-152">**SafeArray(** *Type* **)**</span><span class="sxs-lookup"><span data-stu-id="bc418-152">**SafeArray(** *Type* **)**</span></span>|<span data-ttu-id="bc418-153">**ELEMENT_TYPE_SZARRAY** **\<** *ConvertedType* **>**</span><span class="sxs-lookup"><span data-stu-id="bc418-153">**ELEMENT_TYPE_SZARRAY** **\<** *ConvertedType* **>**</span></span><br /><br /> <span data-ttu-id="bc418-154">Classificação = 1, limite inferior = 0.</span><span class="sxs-lookup"><span data-stu-id="bc418-154">Rank = 1, lower bound = 0.</span></span> <span data-ttu-id="bc418-155">O tamanho é conhecido apenas se é fornecido na assinatura gerenciada.</span><span class="sxs-lookup"><span data-stu-id="bc418-155">Size is known only if provided in the managed signature.</span></span> <span data-ttu-id="bc418-156">Matrizes seguras que não têm a classificação = 1 ou o limite inferior = 0 não podem ter o marshaling realizado como **SZARRAY**.</span><span class="sxs-lookup"><span data-stu-id="bc418-156">Safe arrays that are not rank = 1 or lower bound = 0 cannot be marshaled as **SZARRAY**.</span></span>|  
|<span data-ttu-id="bc418-157">*Tipo*  **[]**</span><span class="sxs-lookup"><span data-stu-id="bc418-157">*Type*  **[]**</span></span>|<span data-ttu-id="bc418-158">**ELEMENT_TYPE_SZARRAY** **\<** *ConvertedType* **>**</span><span class="sxs-lookup"><span data-stu-id="bc418-158">**ELEMENT_TYPE_SZARRAY** **\<** *ConvertedType* **>**</span></span><br /><br /> <span data-ttu-id="bc418-159">Classificação = 1, limite inferior = 0.</span><span class="sxs-lookup"><span data-stu-id="bc418-159">Rank = 1, lower bound = 0.</span></span> <span data-ttu-id="bc418-160">O tamanho é conhecido apenas se é fornecido na assinatura gerenciada.</span><span class="sxs-lookup"><span data-stu-id="bc418-160">Size is known only if provided in the managed signature.</span></span>|  
  
### <a name="safe-arrays"></a><span data-ttu-id="bc418-161">Matrizes seguras</span><span class="sxs-lookup"><span data-stu-id="bc418-161">Safe Arrays</span></span>  
 <span data-ttu-id="bc418-162">Quando uma matriz segura é importada de uma biblioteca de tipos para um assembly .NET, a matriz é convertida em uma matriz unidimensional de um tipo conhecido (como **int**).</span><span class="sxs-lookup"><span data-stu-id="bc418-162">When a safe array is imported from a type library to a .NET assembly, the array is converted to a one-dimensional array of a known type (such as **int**).</span></span> <span data-ttu-id="bc418-163">As mesmas regras de conversão de tipo que se aplicam a parâmetros também se aplicam a elementos de matriz.</span><span class="sxs-lookup"><span data-stu-id="bc418-163">The same type conversion rules that apply to parameters also apply to array elements.</span></span> <span data-ttu-id="bc418-164">Por exemplo, uma matriz segura de tipos **BSTR** torna-se uma matriz gerenciada de cadeias de caracteres e uma matriz segura de variantes torna-se uma matriz gerenciada de objetos.</span><span class="sxs-lookup"><span data-stu-id="bc418-164">For example, a safe array of **BSTR** types becomes a managed array of strings and a safe array of variants becomes a managed array of objects.</span></span> <span data-ttu-id="bc418-165">O tipo de elemento **SAFEARRAY** é capturado na biblioteca de tipos e salvo no valor **SAFEARRAY** da enumeração <xref:System.Runtime.InteropServices.UnmanagedType>.</span><span class="sxs-lookup"><span data-stu-id="bc418-165">The **SAFEARRAY** element type is captured from the type library and saved in the **SAFEARRAY** value of the <xref:System.Runtime.InteropServices.UnmanagedType> enumeration.</span></span>  
  
 <span data-ttu-id="bc418-166">Como a classificação e os limites da matriz segura não podem ser determinados na biblioteca de tipos, a classificação é considerada igual a 1 e o limite inferior é considerado igual a 0.</span><span class="sxs-lookup"><span data-stu-id="bc418-166">Because the rank and bounds of the safe array cannot be determined from the type library, the rank is assumed to equal 1 and the lower bound is assumed to equal 0.</span></span> <span data-ttu-id="bc418-167">A classificação e os limites devem ser definidos na assinatura gerenciada produzida pelo [Importador da Biblioteca de Tipos (Tlbimp.exe)](../../../docs/framework/tools/tlbimp-exe-type-library-importer.md).</span><span class="sxs-lookup"><span data-stu-id="bc418-167">The rank and bounds must be defined in the managed signature produced by the [Type Library Importer (Tlbimp.exe)](../../../docs/framework/tools/tlbimp-exe-type-library-importer.md).</span></span> <span data-ttu-id="bc418-168">Se a classificação passada para o método em tempo de execução for diferente, uma <xref:System.Runtime.InteropServices.SafeArrayRankMismatchException> será gerada.</span><span class="sxs-lookup"><span data-stu-id="bc418-168">If the rank passed to the method at run time differs, a <xref:System.Runtime.InteropServices.SafeArrayRankMismatchException> is thrown.</span></span> <span data-ttu-id="bc418-169">Se o tipo da matriz passado em tempo de execução for diferente, uma <xref:System.Runtime.InteropServices.SafeArrayTypeMismatchException> será gerada.</span><span class="sxs-lookup"><span data-stu-id="bc418-169">If the type of the array passed at run time differs, a <xref:System.Runtime.InteropServices.SafeArrayTypeMismatchException> is thrown.</span></span> <span data-ttu-id="bc418-170">O exemplo a seguir mostra matrizes seguras em código gerenciado e não gerenciado.</span><span class="sxs-lookup"><span data-stu-id="bc418-170">The following example shows safe arrays in managed and unmanaged code.</span></span>  
  
 <span data-ttu-id="bc418-171">**Assinatura não gerenciada**</span><span class="sxs-lookup"><span data-stu-id="bc418-171">**Unmanaged signature**</span></span>  
  
```  
HRESULT New1([in] SAFEARRAY( int ) ar);  
HRESULT New2([in] SAFEARRAY( DATE ) ar);  
HRESULT New3([in, out] SAFEARRAY( BSTR ) *ar);  
```  
  
 <span data-ttu-id="bc418-172">**Assinatura gerenciada**</span><span class="sxs-lookup"><span data-stu-id="bc418-172">**Managed signature**</span></span>  
  
```vb  
Sub New1(<MarshalAs(UnmanagedType.SafeArray, SafeArraySubType:=VT_I4)> _  
   ar() As Integer)  
Sub New2(<MarshalAs(UnmanagedType.SafeArray, SafeArraySubType:=VT_DATE)> _   
   ar() As DateTime)  
Sub New3(ByRef <MarshalAs(UnmanagedType.SafeArray, SafeArraySubType:=VT_BSTR)> _   
   ar() As String)  
```  
  
```csharp  
void New1([MarshalAs(UnmanagedType.SafeArray, SafeArraySubType=VT_I4)] int[] ar) ;  
void New2([MarshalAs(UnmanagedType.SafeArray, SafeArraySubType=VT_DATE)]   
   DateTime[] ar);  
void New3([MarshalAs(UnmanagedType.SafeArray, SafeArraySubType=VT_BSTR)]   
   ref String[] ar);  
```  
  
 <span data-ttu-id="bc418-173">As matrizes seguras multidimensionais ou com limite diferente de zero, poderão ter o marshaling realizado em código gerenciado se a assinatura do método produzida por Tlbimp.exe for modificada para indicar um tipo de elemento **ELEMENT_TYPE_ARRAY** em vez de **ELEMENT_TYPE_SZARRAY**.</span><span class="sxs-lookup"><span data-stu-id="bc418-173">Multidimensional, or nonzero-bound safe arrays, can be marshaled into managed code if the method signature produced by Tlbimp.exe is modified to indicate an element type of **ELEMENT_TYPE_ARRAY** instead of **ELEMENT_TYPE_SZARRAY**.</span></span> <span data-ttu-id="bc418-174">Como alternativa, você pode usar a opção **/sysarray** com Tlbimp.exe para importar todas as matrizes como objetos <xref:System.Array?displayProperty=fullName>.</span><span class="sxs-lookup"><span data-stu-id="bc418-174">Alternatively, you can use the **/sysarray** switch with Tlbimp.exe to import all arrays as <xref:System.Array?displayProperty=fullName> objects.</span></span> <span data-ttu-id="bc418-175">Nos casos em que a matriz que está sendo passada é conhecida como multidimensional, é possível editar o código MSIL (Microsoft Intermediate Language) produzido por Tlbimp.exe e, em seguida, recompilá-lo.</span><span class="sxs-lookup"><span data-stu-id="bc418-175">In cases where the array being passed is known to be multidimensional, you can edit the Microsoft intermediate language (MSIL) code produced by Tlbimp.exe and then recompile it.</span></span> <span data-ttu-id="bc418-176">Para obter detalhes sobre como modificar o código MSIL, consulte [Personalizando RCWs (Runtime Callable Wrappers)](http://msdn.microsoft.com/en-us/4652beaf-77d0-4f37-9687-ca193288c0be).</span><span class="sxs-lookup"><span data-stu-id="bc418-176">For details about how to modify MSIL code, see [Customizing Runtime Callable Wrappers](http://msdn.microsoft.com/en-us/4652beaf-77d0-4f37-9687-ca193288c0be).</span></span>  
  
### <a name="c-style-arrays"></a><span data-ttu-id="bc418-177">Matrizes C-style</span><span class="sxs-lookup"><span data-stu-id="bc418-177">C-Style Arrays</span></span>  
 <span data-ttu-id="bc418-178">Quando uma matriz C-style é importada de uma biblioteca de tipos para um assembly .NET, a matriz é convertida em **ELEMENT_TYPE_SZARRAY**.</span><span class="sxs-lookup"><span data-stu-id="bc418-178">When a C-style array is imported from a type library to a .NET assembly, the array is converted to **ELEMENT_TYPE_SZARRAY**.</span></span>  
  
 <span data-ttu-id="bc418-179">O tipo de elemento da matriz é determinado na biblioteca de tipos e preservado durante a importação.</span><span class="sxs-lookup"><span data-stu-id="bc418-179">The array element type is determined from the type library and preserved during the import.</span></span> <span data-ttu-id="bc418-180">As mesmas regras de conversão que se aplicam a parâmetros também se aplicam a elementos de matriz.</span><span class="sxs-lookup"><span data-stu-id="bc418-180">The same conversion rules that apply to parameters also apply to array elements.</span></span> <span data-ttu-id="bc418-181">Por exemplo, uma matriz de tipos **LPStr** torna-se uma matriz de tipos **String**.</span><span class="sxs-lookup"><span data-stu-id="bc418-181">For example, an array of **LPStr** types becomes an array of **String** types.</span></span> <span data-ttu-id="bc418-182">O Tlbimp.exe captura o tipo de elemento da matriz e aplica o atributo <xref:System.Runtime.InteropServices.MarshalAsAttribute> ao parâmetro.</span><span class="sxs-lookup"><span data-stu-id="bc418-182">Tlbimp.exe captures the array element type and applies the <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribute to the parameter.</span></span>  
  
 <span data-ttu-id="bc418-183">A classificação da matriz é considerada igual a 1.</span><span class="sxs-lookup"><span data-stu-id="bc418-183">The array rank is assumed to equal 1.</span></span> <span data-ttu-id="bc418-184">Se a classificação for maior que 1, a matriz terá o marshaling realizado como uma matriz unidimensional na ordem de coluna principal.</span><span class="sxs-lookup"><span data-stu-id="bc418-184">If the rank is greater than 1, the array is marshaled as a one-dimensional array in column-major order.</span></span> <span data-ttu-id="bc418-185">O limite inferior é sempre igual a 0.</span><span class="sxs-lookup"><span data-stu-id="bc418-185">The lower bound always equals 0.</span></span>  
  
 <span data-ttu-id="bc418-186">As bibliotecas de tipos podem conter matrizes de comprimento fixo ou variável.</span><span class="sxs-lookup"><span data-stu-id="bc418-186">Type libraries can contain arrays of fixed or variable length.</span></span> <span data-ttu-id="bc418-187">O Tlbimp.exe pode importar somente matrizes de comprimento fixo das bibliotecas de tipos porque as bibliotecas de tipos não têm as informações necessárias para realizar marshaling de matrizes de comprimento variável.</span><span class="sxs-lookup"><span data-stu-id="bc418-187">Tlbimp.exe can import only fixed-length arrays from type libraries because type libraries lack the information needed to marshal variable-length arrays.</span></span> <span data-ttu-id="bc418-188">Com matrizes de comprimento fixo, o tamanho é importado da biblioteca de tipos e capturado no **MarshalAsAttribute** aplicado ao parâmetro.</span><span class="sxs-lookup"><span data-stu-id="bc418-188">With fixed-length arrays, the size is imported from the type library and captured in the **MarshalAsAttribute** that is applied to the parameter.</span></span>  
  
 <span data-ttu-id="bc418-189">É necessário definir manualmente as bibliotecas de tipos que contêm matrizes de comprimento variável, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="bc418-189">You must manually define type libraries containing variable-length arrays, as shown in the following example.</span></span>  
  
 <span data-ttu-id="bc418-190">**Assinatura não gerenciada**</span><span class="sxs-lookup"><span data-stu-id="bc418-190">**Unmanaged signature**</span></span>  
  
```  
HRESULT New1(int ar[10]);  
HRESULT New2(double ar[10][20]);  
HRESULT New3(LPWStr ar[10]);  
```  
  
 <span data-ttu-id="bc418-191">**Assinatura gerenciada**</span><span class="sxs-lookup"><span data-stu-id="bc418-191">**Managed signature**</span></span>  
  
```vb  
Sub New1(<MarshalAs(UnmanagedType.LPArray, SizeConst=10)> _  
   ar() As Integer)  
Sub New2(<MarshalAs(UnmanagedType.LPArray, SizeConst=200)> _  
   ar() As Double)  
Sub New2(<MarshalAs(UnmanagedType.LPArray, _  
   ArraySubType=UnmanagedType.LPWStr, SizeConst=10)> _  
   ar() As String)  
```  
  
```csharp  
void New1([MarshalAs(UnmanagedType.LPArray, SizeConst=10)] int[] ar);  
void New2([MarshalAs(UnmanagedType.LPArray, SizeConst=200)] double[] ar);  
void New2([MarshalAs(UnmanagedType.LPArray,   
   ArraySubType=UnmanagedType.LPWStr, SizeConst=10)] String[] ar);  
```  
  
 <span data-ttu-id="bc418-192">Embora seja possível aplicar os atributos **size_is** ou **length_is** a uma matriz na fonte da linguagem IDL para transmitir o tamanho para um cliente, o compilador da linguagem IDL da Microsoft (MIDL) não propaga essas informações para a biblioteca de tipos.</span><span class="sxs-lookup"><span data-stu-id="bc418-192">Although you can apply the **size_is** or **length_is** attributes to an array in Interface Definition Language (IDL) source to convey the size to a client, the Microsoft Interface Definition Language (MIDL) compiler does not propagate that information to the type library.</span></span> <span data-ttu-id="bc418-193">Sem saber o tamanho, o serviço de marshaling de interoperabilidade não pode realizar marshaling dos elementos da matriz.</span><span class="sxs-lookup"><span data-stu-id="bc418-193">Without knowing the size, the interop marshaling service cannot marshal the array elements.</span></span> <span data-ttu-id="bc418-194">Consequentemente, as matrizes de comprimento variável são importadas como argumentos de referência.</span><span class="sxs-lookup"><span data-stu-id="bc418-194">Consequently, variable-length arrays are imported as reference arguments.</span></span> <span data-ttu-id="bc418-195">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="bc418-195">For example:</span></span>  
  
 <span data-ttu-id="bc418-196">**Assinatura não gerenciada**</span><span class="sxs-lookup"><span data-stu-id="bc418-196">**Unmanaged signature**</span></span>  
  
```  
HRESULT New1(int ar[]);  
HRESULT New2(int ArSize, [size_is(ArSize)] double ar[]);  
HRESULT New3(int ElemCnt, [length_is(ElemCnt)] LPStr ar[]);  
```  
  
 <span data-ttu-id="bc418-197">**Assinatura gerenciada**</span><span class="sxs-lookup"><span data-stu-id="bc418-197">**Managed signature**</span></span>  
  
```vb  
Sub New1(ByRef ar As Integer)  
Sub New2(ByRef ar As Double)  
Sub New3(ByRef ar As String)  
```  
  
```csharp  
void New1(ref int ar);    
void New2(ref double ar);    
void New3(ref String ar);   
```  
  
 <span data-ttu-id="bc418-198">É possível fornecer ao marshaler o tamanho da matriz editando o código MSIL (Microsoft Intermediate Language) produzido pelo Tlbimp.exe e, em seguida, recompilá-lo.</span><span class="sxs-lookup"><span data-stu-id="bc418-198">You can provide the marshaler with the array size by editing the Microsoft intermediate language (MSIL) code produced by Tlbimp.exe and then recompiling it.</span></span> <span data-ttu-id="bc418-199">Para obter detalhes sobre como modificar o código MSIL, consulte [Personalizando RCWs (Runtime Callable Wrappers)](http://msdn.microsoft.com/en-us/4652beaf-77d0-4f37-9687-ca193288c0be).</span><span class="sxs-lookup"><span data-stu-id="bc418-199">For details about how to modify MSIL code, see [Customizing Runtime Callable Wrappers](http://msdn.microsoft.com/en-us/4652beaf-77d0-4f37-9687-ca193288c0be).</span></span> <span data-ttu-id="bc418-200">Para indicar o número de elementos na matriz, aplique o tipo <xref:System.Runtime.InteropServices.MarshalAsAttribute> ao parâmetro de matriz da definição de método gerenciado de uma das seguintes maneiras:</span><span class="sxs-lookup"><span data-stu-id="bc418-200">To indicate the number of elements in the array, apply the <xref:System.Runtime.InteropServices.MarshalAsAttribute> type to the array parameter of the managed method definition in one of the following ways:</span></span>  
  
-   <span data-ttu-id="bc418-201">Identifique outro parâmetro que contém o número de elementos na matriz.</span><span class="sxs-lookup"><span data-stu-id="bc418-201">Identify another parameter that contains the number of elements in the array.</span></span> <span data-ttu-id="bc418-202">Os parâmetros são identificados por posição, começando com o primeiro parâmetro como o número 0.</span><span class="sxs-lookup"><span data-stu-id="bc418-202">The parameters are identified by position, starting with the first parameter as number 0.</span></span>     
  
    ```vb  
    Sub [New](ElemCnt As Integer, _  
       \<MarshalAs(UnmanagedType.LPArray, SizeParamIndex:=1)> _  
       ar() As Integer)  
    ```  
  
    ```csharp  
    void New(  
       int ElemCnt,   
       [MarshalAs(UnmanagedType.LPArray, SizeParamIndex=0)] int[] ar );  
    ```  
  
-   <span data-ttu-id="bc418-203">Defina o tamanho da matriz como uma constante.</span><span class="sxs-lookup"><span data-stu-id="bc418-203">Define the size of the array as a constant.</span></span> <span data-ttu-id="bc418-204">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="bc418-204">For example:</span></span>  
  
    ```vb  
    Sub [New](\<MarshalAs(UnmanagedType.LPArray, SizeConst:=128)> _  
       ar() As Integer)  
    ```  
  
    ```csharp  
    void New(  
       [MarshalAs(UnmanagedType.LPArray, SizeConst=128)] int[] ar );  
    ```  
  
 <span data-ttu-id="bc418-205">Ao realizar marshaling de matrizes de código não gerenciado para código gerenciado, o marshaler verifica o **MarshalAsAttribute** associado ao parâmetro para determinar o tamanho da matriz.</span><span class="sxs-lookup"><span data-stu-id="bc418-205">When marshaling arrays from unmanaged code to managed code, the marshaler checks the **MarshalAsAttribute** associated with the parameter to determine the array size.</span></span> <span data-ttu-id="bc418-206">Se o tamanho da matriz não for especificado, somente um elemento terá o marshaling realizado.</span><span class="sxs-lookup"><span data-stu-id="bc418-206">If the array size is not specified, only one element is marshaled.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="bc418-207">O **MarshalAsAttribute** não tem nenhum efeito no marshaling de matrizes gerenciadas para código não gerenciado.</span><span class="sxs-lookup"><span data-stu-id="bc418-207">The **MarshalAsAttribute** has no effect on marshaling managed arrays to unmanaged code.</span></span> <span data-ttu-id="bc418-208">Nessa direção, o tamanho da matriz é determinado pelo exame.</span><span class="sxs-lookup"><span data-stu-id="bc418-208">In that direction, the array size is determined by examination.</span></span> <span data-ttu-id="bc418-209">Não há nenhuma maneira de realizar marshaling de um subconjunto de uma matriz gerenciada.</span><span class="sxs-lookup"><span data-stu-id="bc418-209">There is no way to marshal a subset of a managed array.</span></span>  
  
 <span data-ttu-id="bc418-210">O marshaler de interoperabilidade usa os métodos **CoTaskMemAlloc** e **CoTaskMemFree** para alocar e recuperar a memória.</span><span class="sxs-lookup"><span data-stu-id="bc418-210">The interop marshaler uses the **CoTaskMemAlloc** and **CoTaskMemFree** methods to allocate and retrieve memory.</span></span> <span data-ttu-id="bc418-211">A alocação de memória executada pelo código não gerenciado também deve usar esses métodos.</span><span class="sxs-lookup"><span data-stu-id="bc418-211">Memory allocation performed by unmanaged code must also use these methods.</span></span>  
  
<a name="cpcondefaultmarshalingforarraysanchor4"></a>   
## <a name="passing-arrays-to-com"></a><span data-ttu-id="bc418-212">Passando matrizes para o COM</span><span class="sxs-lookup"><span data-stu-id="bc418-212">Passing Arrays to COM</span></span>  
 <span data-ttu-id="bc418-213">Todos os tipos de matriz gerenciada podem ser passados para um código não gerenciado de um código gerenciado.</span><span class="sxs-lookup"><span data-stu-id="bc418-213">All managed array types can be passed to unmanaged code from managed code.</span></span> <span data-ttu-id="bc418-214">Dependendo do tipo gerenciado e dos atributos aplicados a ele, a matriz pode ser acessada como uma matriz segura ou uma matriz C-style, conforme mostrado na tabela a seguir.</span><span class="sxs-lookup"><span data-stu-id="bc418-214">Depending on the managed type and the attributes applied to it, the array can be accessed as a safe array or a C-style array, as shown in the following table.</span></span>  
  
|<span data-ttu-id="bc418-215">Tipo de matriz gerenciada</span><span class="sxs-lookup"><span data-stu-id="bc418-215">Managed array type</span></span>|<span data-ttu-id="bc418-216">Exportado como</span><span class="sxs-lookup"><span data-stu-id="bc418-216">Exported as</span></span>|  
|------------------------|-----------------|  
|<span data-ttu-id="bc418-217">**ELEMENT_TYPE_SZARRAY** **\<** *type* **>**</span><span class="sxs-lookup"><span data-stu-id="bc418-217">**ELEMENT_TYPE_SZARRAY** **\<** *type* **>**</span></span>|<span data-ttu-id="bc418-218"><xref:System.Runtime.InteropServices.UnmanagedType> **.SafeArray(** *type* **)**</span><span class="sxs-lookup"><span data-stu-id="bc418-218"><xref:System.Runtime.InteropServices.UnmanagedType> **.SafeArray(** *type* **)**</span></span><br /><br /> <span data-ttu-id="bc418-219">**UnmanagedType.LPArray**</span><span class="sxs-lookup"><span data-stu-id="bc418-219">**UnmanagedType.LPArray**</span></span><br /><br /> <span data-ttu-id="bc418-220">O tipo é fornecido na assinatura.</span><span class="sxs-lookup"><span data-stu-id="bc418-220">Type is provided in the signature.</span></span> <span data-ttu-id="bc418-221">A classificação é sempre 1 e o limite inferior é sempre 0.</span><span class="sxs-lookup"><span data-stu-id="bc418-221">Rank is always 1, lower bound is always 0.</span></span> <span data-ttu-id="bc418-222">O tamanho é sempre conhecido em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="bc418-222">Size is always known at run time.</span></span>|  
|<span data-ttu-id="bc418-223">**ELEMENT_TYPE_ARRAY** **\<** *type* **>** **\<** *rank* **>**[**\<** *bounds* **>**]</span><span class="sxs-lookup"><span data-stu-id="bc418-223">**ELEMENT_TYPE_ARRAY** **\<** *type* **>** **\<** *rank* **>**[**\<** *bounds* **>**]</span></span>|<span data-ttu-id="bc418-224">**UnmanagedType.SafeArray(** *type* **)**</span><span class="sxs-lookup"><span data-stu-id="bc418-224">**UnmanagedType.SafeArray(** *type* **)**</span></span><br /><br /> <span data-ttu-id="bc418-225">**UnmanagedType.LPArray**</span><span class="sxs-lookup"><span data-stu-id="bc418-225">**UnmanagedType.LPArray**</span></span><br /><br /> <span data-ttu-id="bc418-226">O tipo, a classificação e os limites são fornecidos na assinatura.</span><span class="sxs-lookup"><span data-stu-id="bc418-226">Type, rank, bounds are provided in the signature.</span></span> <span data-ttu-id="bc418-227">O tamanho é sempre conhecido em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="bc418-227">Size is always known at run time.</span></span>|  
|<span data-ttu-id="bc418-228">**ELEMENT_TYPE_CLASS** **\<**<xref:System.Array?displayProperty=fullName>**>**</span><span class="sxs-lookup"><span data-stu-id="bc418-228">**ELEMENT_TYPE_CLASS** **\<**<xref:System.Array?displayProperty=fullName>**>**</span></span>|<span data-ttu-id="bc418-229">**UT_Interface**</span><span class="sxs-lookup"><span data-stu-id="bc418-229">**UT_Interface**</span></span><br /><br /> <span data-ttu-id="bc418-230">**UnmanagedType.SafeArray(** *type* **)**</span><span class="sxs-lookup"><span data-stu-id="bc418-230">**UnmanagedType.SafeArray(** *type* **)**</span></span><br /><br /> <span data-ttu-id="bc418-231">O tipo, a classificação, os limites e o tamanho são sempre conhecidos em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="bc418-231">Type, rank, bounds, and size are always known at run time.</span></span>|  
  
 <span data-ttu-id="bc418-232">Há uma limitação na Automação OLE relativa a matrizes de estruturas que contêm LPSTR ou LPWSTR.</span><span class="sxs-lookup"><span data-stu-id="bc418-232">There is a limitation in OLE Automation relating to arrays of structures that contain LPSTR or LPWSTR.</span></span>  <span data-ttu-id="bc418-233">Portanto, os campos **String** precisam ter o marshaling realizado como **UnmanagedType.BSTR**.</span><span class="sxs-lookup"><span data-stu-id="bc418-233">Therefore, **String** fields have to be marshaled as **UnmanagedType.BSTR**.</span></span> <span data-ttu-id="bc418-234">Caso contrário, uma exceção será gerada.</span><span class="sxs-lookup"><span data-stu-id="bc418-234">Otherwise, an exception will be thrown.</span></span>  
  
### <a name="elementtypeszarray"></a><span data-ttu-id="bc418-235">ELEMENT_TYPE_SZARRAY</span><span class="sxs-lookup"><span data-stu-id="bc418-235">ELEMENT_TYPE_SZARRAY</span></span>  
 <span data-ttu-id="bc418-236">Quando um método que contém um parâmetro **ELEMENT_TYPE_SZARRAY** (matriz unidimensional) é exportado de um assembly .NET para uma biblioteca de tipos, o parâmetro de matriz é convertido em uma **SAFEARRAY** de determinado tipo.</span><span class="sxs-lookup"><span data-stu-id="bc418-236">When a method containing an **ELEMENT_TYPE_SZARRAY** parameter (one-dimensional array) is exported from a .NET assembly to a type library, the array parameter is converted to a **SAFEARRAY** of a given type.</span></span> <span data-ttu-id="bc418-237">As mesmas regras de conversão se aplicam a tipos de elemento da matriz.</span><span class="sxs-lookup"><span data-stu-id="bc418-237">The same conversion rules apply to the array element types.</span></span> <span data-ttu-id="bc418-238">O conteúdo da matriz gerenciada é copiado automaticamente da memória gerenciada para a **SAFEARRAY**.</span><span class="sxs-lookup"><span data-stu-id="bc418-238">The contents of the managed array are automatically copied from managed memory into the **SAFEARRAY**.</span></span> <span data-ttu-id="bc418-239">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="bc418-239">For example:</span></span>  
  
#### <a name="managed-signature"></a><span data-ttu-id="bc418-240">Assinatura gerenciada</span><span class="sxs-lookup"><span data-stu-id="bc418-240">Managed signature</span></span>  
  
```vb  
Sub [New](ar() As Long)  
Sub [New](ar() As String)  
```  
  
```csharp  
void New(long[] ar );  
void New(String[] ar );  
```  
  
#### <a name="unmanaged-signature"></a><span data-ttu-id="bc418-241">Assinatura não gerenciada</span><span class="sxs-lookup"><span data-stu-id="bc418-241">Unmanaged signature</span></span>  
  
```  
HRESULT New([in] SAFEARRAY( long ) ar);   
HRESULT New([in] SAFEARRAY( BSTR ) ar);  
```  
  
 <span data-ttu-id="bc418-242">A classificação de matrizes seguras é sempre 1 e o limite inferior é sempre 0.</span><span class="sxs-lookup"><span data-stu-id="bc418-242">The rank of the safe arrays is always 1 and the lower bound is always 0.</span></span> <span data-ttu-id="bc418-243">O tamanho é determinado em tempo de execução pelo tamanho da matriz gerenciada que está sendo passada.</span><span class="sxs-lookup"><span data-stu-id="bc418-243">The size is determined at run time by the size of the managed array being passed.</span></span>  
  
 <span data-ttu-id="bc418-244">A matriz também pode ter o marshaling realizado como uma matriz C-style com o uso do atributo <xref:System.Runtime.InteropServices.MarshalAsAttribute>.</span><span class="sxs-lookup"><span data-stu-id="bc418-244">The array can also be marshaled as a C-style array by using the <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribute.</span></span> <span data-ttu-id="bc418-245">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="bc418-245">For example:</span></span>  
  
#### <a name="managed-signature"></a><span data-ttu-id="bc418-246">Assinatura gerenciada</span><span class="sxs-lookup"><span data-stu-id="bc418-246">Managed signature</span></span>  
  
```vb  
Sub [New](<MarshalAs(UnmanagedType.LPArray, SizeParamIndex:=1)> _  
   ar() As Long, size as Integer)  
Sub [New](<MarshalAs(UnmanagedType.LPArray, SizeParamIndex:=1)> _  
   ar() As String, size as Integer)  
Sub [New](<MarshalAs(UnmanagedType.LPArray, _  
   ArraySubType= UnmanagedType.LPStr, SizeParamIndex:=1)> _  
   ar() As String, size as Integer)  
```  
  
```csharp  
void New([MarshalAs(UnmanagedType.LPArray, SizeParamIndex=1)]   
   long [] ar, int size );  
void New([MarshalAs(UnmanagedType.LPArray, SizeParamIndex=1)]   
   String [] ar, int size );  
void New([MarshalAs(UnmanagedType.LPArray, ArraySubType=   
   UnmanagedType.LPStr, SizeParamIndex=1)]   
   String [] ar, int size );  
```  
  
#### <a name="unmanaged-signature"></a><span data-ttu-id="bc418-247">Assinatura não gerenciada</span><span class="sxs-lookup"><span data-stu-id="bc418-247">Unmanaged signature</span></span>  
  
```  
HRESULT New(long ar[]);   
HRESULT New(BSTR ar[]);   
HRESULT New(LPStr ar[]);  
```  
  
 <span data-ttu-id="bc418-248">Embora o marshaler tenha as informações de tamanho necessárias para realizar marshaling da matriz, o tamanho da matriz geralmente é passado como um argumento separado para transmitir o tamanho para o receptor.</span><span class="sxs-lookup"><span data-stu-id="bc418-248">Although the marshaler has the length information needed to marshal the array, the array length is usually passed as a separate argument to convey the length to the callee.</span></span>  
  
### <a name="elementtypearray"></a><span data-ttu-id="bc418-249">ELEMENT_TYPE_ARRAY</span><span class="sxs-lookup"><span data-stu-id="bc418-249">ELEMENT_TYPE_ARRAY</span></span>  
 <span data-ttu-id="bc418-250">Quando um método que contém um parâmetro **ELEMENT_TYPE_ARRAY** é exportado de um assembly .NET para uma biblioteca de tipos, o parâmetro de matriz é convertido em uma **SAFEARRAY** de determinado tipo.</span><span class="sxs-lookup"><span data-stu-id="bc418-250">When a method containing an **ELEMENT_TYPE_ARRAY** parameter is exported from a .NET assembly to a type library, the array parameter is converted to a **SAFEARRAY** of a given type.</span></span> <span data-ttu-id="bc418-251">O conteúdo da matriz gerenciada é copiado automaticamente da memória gerenciada para a **SAFEARRAY**.</span><span class="sxs-lookup"><span data-stu-id="bc418-251">The contents of the managed array are automatically copied from managed memory into the **SAFEARRAY**.</span></span> <span data-ttu-id="bc418-252">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="bc418-252">For example:</span></span>  
  
#### <a name="managed-signature"></a><span data-ttu-id="bc418-253">Assinatura gerenciada</span><span class="sxs-lookup"><span data-stu-id="bc418-253">Managed signature</span></span>  
  
```vb  
Sub [New](ar(,) As Long)  
Sub [New](ar(,) As String)  
```  
  
```csharp  
void New( long [,] ar );  
void New( String [,] ar );  
```  
  
#### <a name="unmanaged-signature"></a><span data-ttu-id="bc418-254">Assinatura não gerenciada</span><span class="sxs-lookup"><span data-stu-id="bc418-254">Unmanaged signature</span></span>  
  
```  
HRESULT New([in] SAFEARRAY( long ) ar);   
HRESULT New([in] SAFEARRAY( BSTR ) ar);  
```  
  
 <span data-ttu-id="bc418-255">A classificação, o tamanho e os limites das matrizes seguras são determinados em tempo de execução pelas características da matriz gerenciada.</span><span class="sxs-lookup"><span data-stu-id="bc418-255">The rank, size, and bounds of the safe arrays are determined at run time by the characteristics of the managed array.</span></span>  
  
 <span data-ttu-id="bc418-256">A matriz também pode ter o marshaling realizado como uma matriz C-style com a aplicação do atributo <xref:System.Runtime.InteropServices.MarshalAsAttribute>.</span><span class="sxs-lookup"><span data-stu-id="bc418-256">The array can also be marshaled as a C-style array by applying the <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribute.</span></span> <span data-ttu-id="bc418-257">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="bc418-257">For example:</span></span>  
  
#### <a name="managed-signature"></a><span data-ttu-id="bc418-258">Assinatura gerenciada</span><span class="sxs-lookup"><span data-stu-id="bc418-258">Managed signature</span></span>  
  
```vb  
Sub [New](<MarshalAs(UnmanagedType.LPARRAY, SizeParamIndex:=1)> _  
   ar(,) As Long, size As Integer)  
Sub [New](<MarshalAs(UnmanagedType.LPARRAY, _  
   ArraySubType:=UnmanagedType.LPStr, SizeParamIndex:=1)> _  
   ar(,) As String, size As Integer)  
```  
  
```csharp  
void New([MarshalAs(UnmanagedType.LPARRAY, SizeParamIndex=1)]   
   long [,] ar, int size );  
void New([MarshalAs(UnmanagedType.LPARRAY,   
   ArraySubType= UnmanagedType.LPStr, SizeParamIndex=1)]   
   String [,] ar, int size );  
```  
  
#### <a name="unmanaged-signature"></a><span data-ttu-id="bc418-259">Assinatura não gerenciada</span><span class="sxs-lookup"><span data-stu-id="bc418-259">Unmanaged signature</span></span>  
  
```  
HRESULT New(long ar[]);   
HRESULT New(LPStr ar[]);  
```  
  
 <span data-ttu-id="bc418-260">Não é possível realizar marshaling de matrizes aninhadas.</span><span class="sxs-lookup"><span data-stu-id="bc418-260">Nested arrays cannot be marshaled.</span></span> <span data-ttu-id="bc418-261">Por exemplo, a assinatura a seguir gera um erro quando exportada com o [Exportador da Biblioteca de Tipos (Tlbexp.exe)](../../../docs/framework/tools/tlbexp-exe-type-library-exporter.md).</span><span class="sxs-lookup"><span data-stu-id="bc418-261">For example, the following signature generates an error when exported with the [Type Library Exporter (Tlbexp.exe)](../../../docs/framework/tools/tlbexp-exe-type-library-exporter.md).</span></span>  
  
#### <a name="managed-signature"></a><span data-ttu-id="bc418-262">Assinatura gerenciada</span><span class="sxs-lookup"><span data-stu-id="bc418-262">Managed signature</span></span>  
  
```vb  
Sub [New](ar()()() As Long)  
```  
  
```csharp  
void New(long [][][] ar );  
```  
  
### <a name="elementtypeclass-systemarray"></a><span data-ttu-id="bc418-263">ELEMENT_TYPE_CLASS \<System.Array></span><span class="sxs-lookup"><span data-stu-id="bc418-263">ELEMENT_TYPE_CLASS \<System.Array></span></span>  
 <span data-ttu-id="bc418-264">Quando um método que contém um parâmetro <xref:System.Array?displayProperty=fullName> é exportado de um assembly .NET para uma biblioteca de tipos, o parâmetro da matriz é convertido em uma interface **_Array**.</span><span class="sxs-lookup"><span data-stu-id="bc418-264">When a method containing a <xref:System.Array?displayProperty=fullName> parameter is exported from a .NET assembly to a type library, the array parameter is converted to an **_Array** interface.</span></span> <span data-ttu-id="bc418-265">O conteúdo da matriz gerenciada é acessível somente por meio dos métodos e das propriedades da interface **_Array**.</span><span class="sxs-lookup"><span data-stu-id="bc418-265">The contents of the managed array are accessible only through the methods and properties of the **_Array** interface.</span></span> <span data-ttu-id="bc418-266">**System.Array** também pode ter o marshaling realizado como uma **SAFEARRAY** usando o atributo <xref:System.Runtime.InteropServices.MarshalAsAttribute>.</span><span class="sxs-lookup"><span data-stu-id="bc418-266">**System.Array** can also be marshaled as a **SAFEARRAY** by using the <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribute.</span></span> <span data-ttu-id="bc418-267">Ao ter o marshaling realizado como uma matriz segura, os elementos da matriz têm o marshaling realizado como variantes.</span><span class="sxs-lookup"><span data-stu-id="bc418-267">When marshaled as a safe array, the array elements are marshaled as variants.</span></span> <span data-ttu-id="bc418-268">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="bc418-268">For example:</span></span>  
  
#### <a name="managed-signature"></a><span data-ttu-id="bc418-269">Assinatura gerenciada</span><span class="sxs-lookup"><span data-stu-id="bc418-269">Managed signature</span></span>  
  
```vb  
Sub New1( ar As System.Array )  
Sub New2( <MarshalAs(UnmanagedType.Safe array)> ar As System.Array )  
```  
  
```csharp  
void New1( System.Array ar );  
void New2( [MarshalAs(UnmanagedType.Safe array)] System.Array ar );  
```  
  
#### <a name="unmanaged-signature"></a><span data-ttu-id="bc418-270">Assinatura não gerenciada</span><span class="sxs-lookup"><span data-stu-id="bc418-270">Unmanaged signature</span></span>  
  
```  
HRESULT New([in] _Array *ar);   
HRESULT New([in] SAFEARRAY(VARIANT) ar);  
```  
  
### <a name="arrays-within-structures"></a><span data-ttu-id="bc418-271">Matrizes em estruturas</span><span class="sxs-lookup"><span data-stu-id="bc418-271">Arrays within Structures</span></span>  
 <span data-ttu-id="bc418-272">Estruturas não gerenciadas podem conter matrizes inseridas.</span><span class="sxs-lookup"><span data-stu-id="bc418-272">Unmanaged structures can contain embedded arrays.</span></span> <span data-ttu-id="bc418-273">Por padrão, esses campos de matriz inseridos têm o marshaling realizado como uma SAFEARRAY.</span><span class="sxs-lookup"><span data-stu-id="bc418-273">By default, these embedded array fields are marshaled as a SAFEARRAY.</span></span> <span data-ttu-id="bc418-274">No exemplo a seguir, `s1` é uma matriz inserida que é alocada diretamente na própria estrutura.</span><span class="sxs-lookup"><span data-stu-id="bc418-274">In the following example, `s1` is an embedded array that is allocated directly within the structure itself.</span></span>  
  
#### <a name="unmanaged-representation"></a><span data-ttu-id="bc418-275">Representação não gerenciada</span><span class="sxs-lookup"><span data-stu-id="bc418-275">Unmanaged representation</span></span>  
  
```  
struct MyStruct {  
    short s1[128];  
}  
```  
  
 <span data-ttu-id="bc418-276">Matrizes podem ter o marshaling realizado como <xref:System.Runtime.InteropServices.UnmanagedType>, o que exige a definição do campo <xref:System.Runtime.InteropServices.MarshalAsAttribute>.</span><span class="sxs-lookup"><span data-stu-id="bc418-276">Arrays can be marshaled as <xref:System.Runtime.InteropServices.UnmanagedType>, which requires you to set the <xref:System.Runtime.InteropServices.MarshalAsAttribute> field.</span></span> <span data-ttu-id="bc418-277">O tamanho pode ser definido somente como uma constante.</span><span class="sxs-lookup"><span data-stu-id="bc418-277">The size can be set only as a constant.</span></span> <span data-ttu-id="bc418-278">O código a seguir mostra a definição gerenciada correspondente de `MyStruct`.</span><span class="sxs-lookup"><span data-stu-id="bc418-278">The following code shows the corresponding managed definition of `MyStruct`.</span></span>  
  
```vb  
Public Structure <StructLayout(LayoutKind.Sequential)> MyStruct  
   Public <MarshalAs(UnmanagedType.ByValArray, SizeConst := 128)> _  
     s1() As Short  
End Structure  
```  
  
```csharp  
[StructLayout(LayoutKind.Sequential)]  
public struct MyStruct {  
   [MarshalAs(UnmanagedType.ByValArray, SizeConst=128)] public short[] s1;  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="bc418-279">Consulte também</span><span class="sxs-lookup"><span data-stu-id="bc418-279">See Also</span></span>  
 <span data-ttu-id="bc418-280">[Comportamento de marshaling padrão](../../../docs/framework/interop/default-marshaling-behavior.md) </span><span class="sxs-lookup"><span data-stu-id="bc418-280">[Default Marshaling Behavior](../../../docs/framework/interop/default-marshaling-behavior.md) </span></span>  
 <span data-ttu-id="bc418-281">[Tipos blittable e não blittable](../../../docs/framework/interop/blittable-and-non-blittable-types.md) </span><span class="sxs-lookup"><span data-stu-id="bc418-281">[Blittable and Non-Blittable Types](../../../docs/framework/interop/blittable-and-non-blittable-types.md) </span></span>  
 <span data-ttu-id="bc418-282">[Atributos direcionais](http://msdn.microsoft.com/en-us/241ac5b5-928e-4969-8f58-1dbc048f9ea2) </span><span class="sxs-lookup"><span data-stu-id="bc418-282">[Directional Attributes](http://msdn.microsoft.com/en-us/241ac5b5-928e-4969-8f58-1dbc048f9ea2) </span></span>  
 [<span data-ttu-id="bc418-283">Copiando e fixando</span><span class="sxs-lookup"><span data-stu-id="bc418-283">Copying and Pinning</span></span>](../../../docs/framework/interop/copying-and-pinning.md)

