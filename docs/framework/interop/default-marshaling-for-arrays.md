---
title: Marshaling padrão para matrizes
description: Entender o marshaling padrão para matrizes. Examine matrizes gerenciadas, matrizes não gerenciadas, passando parâmetros de matriz para código .NET e passando matrizes para COM.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- interop marshaling, arrays
- arrays, interop marshaling
ms.assetid: 8a3cca8b-dd94-4e3d-ad9a-9ee7590654bc
ms.openlocfilehash: 6bfe95576a6460efac75fd392e24acf42e36f2de
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90555257"
---
# <a name="default-marshaling-for-arrays"></a><span data-ttu-id="09c9e-104">Marshaling padrão para matrizes</span><span class="sxs-lookup"><span data-stu-id="09c9e-104">Default Marshaling for Arrays</span></span>
<span data-ttu-id="09c9e-105">Em um aplicativo que consiste inteiramente em um código gerenciado, o Common Language Runtime passa tipos de matriz como parâmetros de Entrada/Saída.</span><span class="sxs-lookup"><span data-stu-id="09c9e-105">In an application consisting entirely of managed code, the common language runtime passes array types as In/Out parameters.</span></span> <span data-ttu-id="09c9e-106">Por outro lado, o marshaler de interoperabilidade passa uma matriz como parâmetros de Entrada, por padrão.</span><span class="sxs-lookup"><span data-stu-id="09c9e-106">In contrast, the interop marshaler passes an array as In parameters by default.</span></span>  
  
 <span data-ttu-id="09c9e-107">Com a [otimização de anexação](copying-and-pinning.md), uma matriz blittable pode aparecer operar como um parâmetro de Entrada/Saída ao interagir com objetos no mesmo apartment.</span><span class="sxs-lookup"><span data-stu-id="09c9e-107">With [pinning optimization](copying-and-pinning.md), a blittable array can appear to operate as an In/Out parameter when interacting with objects in the same apartment.</span></span> <span data-ttu-id="09c9e-108">No entanto, se você exportar o código posteriormente para uma biblioteca de tipos usada para gerar o proxy entre computadores e essa biblioteca for usada para realizar marshaling das chamadas entre apartments, as chamadas poderão reverter como verdadeiro o comportamento do parâmetro de Entrada.</span><span class="sxs-lookup"><span data-stu-id="09c9e-108">However, if you later export the code to a type library used to generate the cross-machine proxy, and that library is used to marshal your calls across apartments, the calls can revert to true In parameter behavior.</span></span>  
  
 <span data-ttu-id="09c9e-109">Matrizes são complexas por natureza e as distinções entre matrizes gerenciadas e não gerenciadas garantem mais informações do que outros tipos não blittable.</span><span class="sxs-lookup"><span data-stu-id="09c9e-109">Arrays are complex by nature, and the distinctions between managed and unmanaged arrays warrant more information than other non-blittable types.</span></span>  
  
## <a name="managed-arrays"></a><span data-ttu-id="09c9e-110">Matrizes gerenciadas</span><span class="sxs-lookup"><span data-stu-id="09c9e-110">Managed Arrays</span></span>  
 <span data-ttu-id="09c9e-111">Os tipos de matriz gerenciada podem variar; no entanto, a classe <xref:System.Array?displayProperty=nameWithType> é a classe base de todos os tipos de matriz.</span><span class="sxs-lookup"><span data-stu-id="09c9e-111">Managed array types can vary; however, the <xref:System.Array?displayProperty=nameWithType> class is the base class of all array types.</span></span> <span data-ttu-id="09c9e-112">A classe **System.Array** tem propriedades para determinar a classificação, o tamanho e os limites inferior e superior de uma matriz, bem como métodos para acessar, classificar, pesquisar, copiar e criar matrizes.</span><span class="sxs-lookup"><span data-stu-id="09c9e-112">The **System.Array** class has properties for determining the rank, length, and lower and upper bounds of an array, as well as methods for accessing, sorting, searching, copying, and creating arrays.</span></span>  
  
 <span data-ttu-id="09c9e-113">Esses tipos de matriz são dinâmicos e não tem um tipo estático correspondente definido na biblioteca de classes base.</span><span class="sxs-lookup"><span data-stu-id="09c9e-113">These array types are dynamic and do not have a corresponding static type defined in the base class library.</span></span> <span data-ttu-id="09c9e-114">É conveniente pensar em cada combinação de tipo de elemento e classificação como um tipo distinto de matriz.</span><span class="sxs-lookup"><span data-stu-id="09c9e-114">It is convenient to think of each combination of element type and rank as a distinct type of array.</span></span> <span data-ttu-id="09c9e-115">Portanto, uma matriz unidimensional de inteiros é de um tipo diferente do que uma matriz unidimensional de tipos double.</span><span class="sxs-lookup"><span data-stu-id="09c9e-115">Therefore, a one-dimensional array of integers is of a different type than a one-dimensional array of double types.</span></span> <span data-ttu-id="09c9e-116">Da mesma forma, uma matriz bidimensional de inteiros é diferente de uma matriz unidimensional de inteiros.</span><span class="sxs-lookup"><span data-stu-id="09c9e-116">Similarly a two-dimensional array of integers is different from a one-dimensional array of integers.</span></span> <span data-ttu-id="09c9e-117">Os limites da matriz não são considerados durante a comparação de tipos.</span><span class="sxs-lookup"><span data-stu-id="09c9e-117">The bounds of the array are not considered when comparing types.</span></span>  
  
 <span data-ttu-id="09c9e-118">Como mostra a tabela a seguir, qualquer instância de uma matriz gerenciada deve ser de um tipo de elemento, classificação e limite inferior específicos.</span><span class="sxs-lookup"><span data-stu-id="09c9e-118">As the following table shows, any instance of a managed array must be of a specific element type, rank, and lower bound.</span></span>  
  
|<span data-ttu-id="09c9e-119">Tipo de matriz gerenciada</span><span class="sxs-lookup"><span data-stu-id="09c9e-119">Managed array type</span></span>|<span data-ttu-id="09c9e-120">Tipo de elemento</span><span class="sxs-lookup"><span data-stu-id="09c9e-120">Element type</span></span>|<span data-ttu-id="09c9e-121">Rank</span><span class="sxs-lookup"><span data-stu-id="09c9e-121">Rank</span></span>|<span data-ttu-id="09c9e-122">Limite inferior</span><span class="sxs-lookup"><span data-stu-id="09c9e-122">Lower bound</span></span>|<span data-ttu-id="09c9e-123">Notação de assinatura</span><span class="sxs-lookup"><span data-stu-id="09c9e-123">Signature notation</span></span>|  
|------------------------|------------------|----------|-----------------|------------------------|  
|<span data-ttu-id="09c9e-124">**ELEMENT_TYPE_ARRAY**</span><span class="sxs-lookup"><span data-stu-id="09c9e-124">**ELEMENT_TYPE_ARRAY**</span></span>|<span data-ttu-id="09c9e-125">Especificado pelo tipo.</span><span class="sxs-lookup"><span data-stu-id="09c9e-125">Specified by type.</span></span>|<span data-ttu-id="09c9e-126">Especificado pela classificação.</span><span class="sxs-lookup"><span data-stu-id="09c9e-126">Specified by rank.</span></span>|<span data-ttu-id="09c9e-127">Opcionalmente, especificado pelos limites.</span><span class="sxs-lookup"><span data-stu-id="09c9e-127">Optionally specified by bounds.</span></span>|<span data-ttu-id="09c9e-128">*tipo* **[** *n*,*m* **]**</span><span class="sxs-lookup"><span data-stu-id="09c9e-128">*type* **[** *n*,*m* **]**</span></span>|  
|<span data-ttu-id="09c9e-129">**ELEMENT_TYPE_CLASS**</span><span class="sxs-lookup"><span data-stu-id="09c9e-129">**ELEMENT_TYPE_CLASS**</span></span>|<span data-ttu-id="09c9e-130">Unknown</span><span class="sxs-lookup"><span data-stu-id="09c9e-130">Unknown</span></span>|<span data-ttu-id="09c9e-131">Unknown</span><span class="sxs-lookup"><span data-stu-id="09c9e-131">Unknown</span></span>|<span data-ttu-id="09c9e-132">Unknown</span><span class="sxs-lookup"><span data-stu-id="09c9e-132">Unknown</span></span>|<span data-ttu-id="09c9e-133">**System.Array**</span><span class="sxs-lookup"><span data-stu-id="09c9e-133">**System.Array**</span></span>|  
|<span data-ttu-id="09c9e-134">**ELEMENT_TYPE_SZARRAY**</span><span class="sxs-lookup"><span data-stu-id="09c9e-134">**ELEMENT_TYPE_SZARRAY**</span></span>|<span data-ttu-id="09c9e-135">Especificado pelo tipo.</span><span class="sxs-lookup"><span data-stu-id="09c9e-135">Specified by type.</span></span>|<span data-ttu-id="09c9e-136">1</span><span class="sxs-lookup"><span data-stu-id="09c9e-136">1</span></span>|<span data-ttu-id="09c9e-137">0</span><span class="sxs-lookup"><span data-stu-id="09c9e-137">0</span></span>|<span data-ttu-id="09c9e-138">*tipo* **[** *n* **]**</span><span class="sxs-lookup"><span data-stu-id="09c9e-138">*type* **[** *n* **]**</span></span>|  
  
## <a name="unmanaged-arrays"></a><span data-ttu-id="09c9e-139">Matrizes não gerenciadas</span><span class="sxs-lookup"><span data-stu-id="09c9e-139">Unmanaged Arrays</span></span>  
 <span data-ttu-id="09c9e-140">Matrizes não gerenciadas são matrizes seguras de estilo COM ou matrizes C-style com comprimento fixo ou variável.</span><span class="sxs-lookup"><span data-stu-id="09c9e-140">Unmanaged arrays are either COM-style safe arrays or C-style arrays with fixed or variable length.</span></span> <span data-ttu-id="09c9e-141">Matrizes seguras são matrizes autodescritivas que levam o tipo, a classificação e os limites dos dados da matriz associada.</span><span class="sxs-lookup"><span data-stu-id="09c9e-141">Safe arrays are self-describing arrays that carry the type, rank, and bounds of the associated array data.</span></span> <span data-ttu-id="09c9e-142">Matrizes C-style são matrizes tipadas unidimensionais com um limite inferior fixo igual a 0.</span><span class="sxs-lookup"><span data-stu-id="09c9e-142">C-style arrays are one-dimensional typed arrays with a fixed lower bound of 0.</span></span> <span data-ttu-id="09c9e-143">O serviço de marshaling tem suporte limitado para ambos os tipos de matrizes.</span><span class="sxs-lookup"><span data-stu-id="09c9e-143">The marshaling service has limited support for both types of arrays.</span></span>  
  
## <a name="passing-array-parameters-to-net-code"></a><span data-ttu-id="09c9e-144">Passando parâmetros de matriz para um código do .NET</span><span class="sxs-lookup"><span data-stu-id="09c9e-144">Passing Array Parameters to .NET Code</span></span>  
 <span data-ttu-id="09c9e-145">As matrizes C-style e as matrizes seguras podem ser passadas para um código do .NET de um código não gerenciado, como uma matriz segura ou uma matriz C-style.</span><span class="sxs-lookup"><span data-stu-id="09c9e-145">Both C-style arrays and safe arrays can be passed to .NET code from unmanaged code as either a safe array or a C-style array.</span></span> <span data-ttu-id="09c9e-146">A tabela a seguir mostra o valor de tipo não gerenciado e o tipo importado.</span><span class="sxs-lookup"><span data-stu-id="09c9e-146">The following table shows the unmanaged type value and the imported type.</span></span>  
  
|<span data-ttu-id="09c9e-147">Tipo não gerenciado</span><span class="sxs-lookup"><span data-stu-id="09c9e-147">Unmanaged type</span></span>|<span data-ttu-id="09c9e-148">Tipo importado</span><span class="sxs-lookup"><span data-stu-id="09c9e-148">Imported type</span></span>|  
|--------------------|-------------------|  
|<span data-ttu-id="09c9e-149">**SafeArray (** *tipo* **)**</span><span class="sxs-lookup"><span data-stu-id="09c9e-149">**SafeArray(** *Type* **)**</span></span>|<span data-ttu-id="09c9e-150">**ELEMENT_TYPE_SZARRAY\*\*\*\*\<** *ConvertedType* **>**</span><span class="sxs-lookup"><span data-stu-id="09c9e-150">**ELEMENT_TYPE_SZARRAY** **\<** *ConvertedType* **>**</span></span><br /><br /> <span data-ttu-id="09c9e-151">Classificação = 1, limite inferior = 0.</span><span class="sxs-lookup"><span data-stu-id="09c9e-151">Rank = 1, lower bound = 0.</span></span> <span data-ttu-id="09c9e-152">O tamanho é conhecido apenas se é fornecido na assinatura gerenciada.</span><span class="sxs-lookup"><span data-stu-id="09c9e-152">Size is known only if provided in the managed signature.</span></span> <span data-ttu-id="09c9e-153">Matrizes seguras que não têm a classificação = 1 ou o limite inferior = 0 não podem ter o marshaling realizado como **SZARRAY**.</span><span class="sxs-lookup"><span data-stu-id="09c9e-153">Safe arrays that are not rank = 1 or lower bound = 0 cannot be marshaled as **SZARRAY**.</span></span>|  
|<span data-ttu-id="09c9e-154">*Tipo*  **[]**</span><span class="sxs-lookup"><span data-stu-id="09c9e-154">*Type*  **[]**</span></span>|<span data-ttu-id="09c9e-155">**ELEMENT_TYPE_SZARRAY\*\*\*\*\<** *ConvertedType* **>**</span><span class="sxs-lookup"><span data-stu-id="09c9e-155">**ELEMENT_TYPE_SZARRAY** **\<** *ConvertedType* **>**</span></span><br /><br /> <span data-ttu-id="09c9e-156">Classificação = 1, limite inferior = 0.</span><span class="sxs-lookup"><span data-stu-id="09c9e-156">Rank = 1, lower bound = 0.</span></span> <span data-ttu-id="09c9e-157">O tamanho é conhecido apenas se é fornecido na assinatura gerenciada.</span><span class="sxs-lookup"><span data-stu-id="09c9e-157">Size is known only if provided in the managed signature.</span></span>|  
  
### <a name="safe-arrays"></a><span data-ttu-id="09c9e-158">Matrizes seguras</span><span class="sxs-lookup"><span data-stu-id="09c9e-158">Safe Arrays</span></span>  
 <span data-ttu-id="09c9e-159">Quando uma matriz segura é importada de uma biblioteca de tipos para um assembly .NET, a matriz é convertida em uma matriz unidimensional de um tipo conhecido (como **int**).</span><span class="sxs-lookup"><span data-stu-id="09c9e-159">When a safe array is imported from a type library to a .NET assembly, the array is converted to a one-dimensional array of a known type (such as **int**).</span></span> <span data-ttu-id="09c9e-160">As mesmas regras de conversão de tipo que se aplicam a parâmetros também se aplicam a elementos de matriz.</span><span class="sxs-lookup"><span data-stu-id="09c9e-160">The same type conversion rules that apply to parameters also apply to array elements.</span></span> <span data-ttu-id="09c9e-161">Por exemplo, uma matriz segura de tipos **BSTR** torna-se uma matriz gerenciada de cadeias de caracteres e uma matriz segura de variantes torna-se uma matriz gerenciada de objetos.</span><span class="sxs-lookup"><span data-stu-id="09c9e-161">For example, a safe array of **BSTR** types becomes a managed array of strings and a safe array of variants becomes a managed array of objects.</span></span> <span data-ttu-id="09c9e-162">O tipo de elemento **SAFEARRAY** é capturado na biblioteca de tipos e salvo no valor **SAFEARRAY** da enumeração <xref:System.Runtime.InteropServices.UnmanagedType>.</span><span class="sxs-lookup"><span data-stu-id="09c9e-162">The **SAFEARRAY** element type is captured from the type library and saved in the **SAFEARRAY** value of the <xref:System.Runtime.InteropServices.UnmanagedType> enumeration.</span></span>  
  
 <span data-ttu-id="09c9e-163">Como a classificação e os limites da matriz segura não podem ser determinados na biblioteca de tipos, a classificação é considerada igual a 1 e o limite inferior é considerado igual a 0.</span><span class="sxs-lookup"><span data-stu-id="09c9e-163">Because the rank and bounds of the safe array cannot be determined from the type library, the rank is assumed to equal 1 and the lower bound is assumed to equal 0.</span></span> <span data-ttu-id="09c9e-164">A classificação e os limites devem ser definidos na assinatura gerenciada produzida pelo [Importador da Biblioteca de Tipos (Tlbimp.exe)](../tools/tlbimp-exe-type-library-importer.md).</span><span class="sxs-lookup"><span data-stu-id="09c9e-164">The rank and bounds must be defined in the managed signature produced by the [Type Library Importer (Tlbimp.exe)](../tools/tlbimp-exe-type-library-importer.md).</span></span> <span data-ttu-id="09c9e-165">Se a classificação passada para o método em tempo de execução for diferente, uma <xref:System.Runtime.InteropServices.SafeArrayRankMismatchException> será gerada.</span><span class="sxs-lookup"><span data-stu-id="09c9e-165">If the rank passed to the method at run time differs, a <xref:System.Runtime.InteropServices.SafeArrayRankMismatchException> is thrown.</span></span> <span data-ttu-id="09c9e-166">Se o tipo da matriz passado em tempo de execução for diferente, uma <xref:System.Runtime.InteropServices.SafeArrayTypeMismatchException> será gerada.</span><span class="sxs-lookup"><span data-stu-id="09c9e-166">If the type of the array passed at run time differs, a <xref:System.Runtime.InteropServices.SafeArrayTypeMismatchException> is thrown.</span></span> <span data-ttu-id="09c9e-167">O exemplo a seguir mostra matrizes seguras em código gerenciado e não gerenciado.</span><span class="sxs-lookup"><span data-stu-id="09c9e-167">The following example shows safe arrays in managed and unmanaged code.</span></span>  
  
 <span data-ttu-id="09c9e-168">**Assinatura não gerenciada**</span><span class="sxs-lookup"><span data-stu-id="09c9e-168">**Unmanaged signature**</span></span>  
  
```cpp
HRESULT New1([in] SAFEARRAY( int ) ar);  
HRESULT New2([in] SAFEARRAY( DATE ) ar);  
HRESULT New3([in, out] SAFEARRAY( BSTR ) *ar);  
```  
  
 <span data-ttu-id="09c9e-169">**Assinatura gerenciada**</span><span class="sxs-lookup"><span data-stu-id="09c9e-169">**Managed signature**</span></span>  
  
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
  
 <span data-ttu-id="09c9e-170">As matrizes seguras multidimensionais ou com limite diferente de zero, poderão ter o marshaling realizado em código gerenciado se a assinatura do método produzida por Tlbimp.exe for modificada para indicar um tipo de elemento **ELEMENT_TYPE_ARRAY** em vez de **ELEMENT_TYPE_SZARRAY**.</span><span class="sxs-lookup"><span data-stu-id="09c9e-170">Multidimensional, or nonzero-bound safe arrays, can be marshaled into managed code if the method signature produced by Tlbimp.exe is modified to indicate an element type of **ELEMENT_TYPE_ARRAY** instead of **ELEMENT_TYPE_SZARRAY**.</span></span> <span data-ttu-id="09c9e-171">Como alternativa, você pode usar a opção **/sysarray** com Tlbimp.exe para importar todas as matrizes como objetos <xref:System.Array?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="09c9e-171">Alternatively, you can use the **/sysarray** switch with Tlbimp.exe to import all arrays as <xref:System.Array?displayProperty=nameWithType> objects.</span></span> <span data-ttu-id="09c9e-172">Nos casos em que a matriz que está sendo passada é conhecida como multidimensional, é possível editar o código MSIL (Microsoft Intermediate Language) produzido por Tlbimp.exe e, em seguida, recompilá-lo.</span><span class="sxs-lookup"><span data-stu-id="09c9e-172">In cases where the array being passed is known to be multidimensional, you can edit the Microsoft intermediate language (MSIL) code produced by Tlbimp.exe and then recompile it.</span></span> <span data-ttu-id="09c9e-173">Para obter detalhes sobre como modificar o código MSIL, consulte [Personalizando RCWs (Runtime Callable Wrappers)](/previous-versions/dotnet/netframework-4.0/e753eftz(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="09c9e-173">For details about how to modify MSIL code, see [Customizing Runtime Callable Wrappers](/previous-versions/dotnet/netframework-4.0/e753eftz(v=vs.100)).</span></span>  
  
### <a name="c-style-arrays"></a><span data-ttu-id="09c9e-174">Matrizes C-style</span><span class="sxs-lookup"><span data-stu-id="09c9e-174">C-Style Arrays</span></span>  
 <span data-ttu-id="09c9e-175">Quando uma matriz C-style é importada de uma biblioteca de tipos para um assembly .NET, a matriz é convertida em **ELEMENT_TYPE_SZARRAY**.</span><span class="sxs-lookup"><span data-stu-id="09c9e-175">When a C-style array is imported from a type library to a .NET assembly, the array is converted to **ELEMENT_TYPE_SZARRAY**.</span></span>  
  
 <span data-ttu-id="09c9e-176">O tipo de elemento da matriz é determinado na biblioteca de tipos e preservado durante a importação.</span><span class="sxs-lookup"><span data-stu-id="09c9e-176">The array element type is determined from the type library and preserved during the import.</span></span> <span data-ttu-id="09c9e-177">As mesmas regras de conversão que se aplicam a parâmetros também se aplicam a elementos de matriz.</span><span class="sxs-lookup"><span data-stu-id="09c9e-177">The same conversion rules that apply to parameters also apply to array elements.</span></span> <span data-ttu-id="09c9e-178">Por exemplo, uma matriz de tipos **LPStr** torna-se uma matriz de tipos **String**.</span><span class="sxs-lookup"><span data-stu-id="09c9e-178">For example, an array of **LPStr** types becomes an array of **String** types.</span></span> <span data-ttu-id="09c9e-179">O Tlbimp.exe captura o tipo de elemento da matriz e aplica o atributo <xref:System.Runtime.InteropServices.MarshalAsAttribute> ao parâmetro.</span><span class="sxs-lookup"><span data-stu-id="09c9e-179">Tlbimp.exe captures the array element type and applies the <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribute to the parameter.</span></span>  
  
 <span data-ttu-id="09c9e-180">A classificação da matriz é considerada igual a 1.</span><span class="sxs-lookup"><span data-stu-id="09c9e-180">The array rank is assumed to equal 1.</span></span> <span data-ttu-id="09c9e-181">Se a classificação for maior que 1, a matriz terá o marshaling realizado como uma matriz unidimensional na ordem de coluna principal.</span><span class="sxs-lookup"><span data-stu-id="09c9e-181">If the rank is greater than 1, the array is marshaled as a one-dimensional array in column-major order.</span></span> <span data-ttu-id="09c9e-182">O limite inferior é sempre igual a 0.</span><span class="sxs-lookup"><span data-stu-id="09c9e-182">The lower bound always equals 0.</span></span>  
  
 <span data-ttu-id="09c9e-183">As bibliotecas de tipos podem conter matrizes de comprimento fixo ou variável.</span><span class="sxs-lookup"><span data-stu-id="09c9e-183">Type libraries can contain arrays of fixed or variable length.</span></span> <span data-ttu-id="09c9e-184">O Tlbimp.exe pode importar somente matrizes de comprimento fixo das bibliotecas de tipos porque as bibliotecas de tipos não têm as informações necessárias para realizar marshaling de matrizes de comprimento variável.</span><span class="sxs-lookup"><span data-stu-id="09c9e-184">Tlbimp.exe can import only fixed-length arrays from type libraries because type libraries lack the information needed to marshal variable-length arrays.</span></span> <span data-ttu-id="09c9e-185">Com matrizes de comprimento fixo, o tamanho é importado da biblioteca de tipos e capturado no **MarshalAsAttribute** aplicado ao parâmetro.</span><span class="sxs-lookup"><span data-stu-id="09c9e-185">With fixed-length arrays, the size is imported from the type library and captured in the **MarshalAsAttribute** that is applied to the parameter.</span></span>  
  
 <span data-ttu-id="09c9e-186">É necessário definir manualmente as bibliotecas de tipos que contêm matrizes de comprimento variável, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="09c9e-186">You must manually define type libraries containing variable-length arrays, as shown in the following example.</span></span>  
  
 <span data-ttu-id="09c9e-187">**Assinatura não gerenciada**</span><span class="sxs-lookup"><span data-stu-id="09c9e-187">**Unmanaged signature**</span></span>  
  
```cpp
HRESULT New1(int ar[10]);  
HRESULT New2(double ar[10][20]);  
HRESULT New3(LPWStr ar[10]);  
```  
  
 <span data-ttu-id="09c9e-188">**Assinatura gerenciada**</span><span class="sxs-lookup"><span data-stu-id="09c9e-188">**Managed signature**</span></span>  
  
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
  
 <span data-ttu-id="09c9e-189">Embora seja possível aplicar os atributos **size_is** ou **length_is** a uma matriz na fonte da linguagem IDL para transmitir o tamanho para um cliente, o compilador da linguagem IDL da Microsoft (MIDL) não propaga essas informações para a biblioteca de tipos.</span><span class="sxs-lookup"><span data-stu-id="09c9e-189">Although you can apply the **size_is** or **length_is** attributes to an array in Interface Definition Language (IDL) source to convey the size to a client, the Microsoft Interface Definition Language (MIDL) compiler does not propagate that information to the type library.</span></span> <span data-ttu-id="09c9e-190">Sem saber o tamanho, o serviço de marshaling de interoperabilidade não pode realizar marshaling dos elementos da matriz.</span><span class="sxs-lookup"><span data-stu-id="09c9e-190">Without knowing the size, the interop marshaling service cannot marshal the array elements.</span></span> <span data-ttu-id="09c9e-191">Consequentemente, as matrizes de comprimento variável são importadas como argumentos de referência.</span><span class="sxs-lookup"><span data-stu-id="09c9e-191">Consequently, variable-length arrays are imported as reference arguments.</span></span> <span data-ttu-id="09c9e-192">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="09c9e-192">For example:</span></span>  
  
 <span data-ttu-id="09c9e-193">**Assinatura não gerenciada**</span><span class="sxs-lookup"><span data-stu-id="09c9e-193">**Unmanaged signature**</span></span>  
  
```cpp
HRESULT New1(int ar[]);  
HRESULT New2(int ArSize, [size_is(ArSize)] double ar[]);  
HRESULT New3(int ElemCnt, [length_is(ElemCnt)] LPStr ar[]);  
```  
  
 <span data-ttu-id="09c9e-194">**Assinatura gerenciada**</span><span class="sxs-lookup"><span data-stu-id="09c9e-194">**Managed signature**</span></span>  
  
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
  
 <span data-ttu-id="09c9e-195">É possível fornecer ao marshaler o tamanho da matriz editando o código MSIL (Microsoft Intermediate Language) produzido pelo Tlbimp.exe e, em seguida, recompilá-lo.</span><span class="sxs-lookup"><span data-stu-id="09c9e-195">You can provide the marshaler with the array size by editing the Microsoft intermediate language (MSIL) code produced by Tlbimp.exe and then recompiling it.</span></span> <span data-ttu-id="09c9e-196">Para obter detalhes sobre como modificar o código MSIL, consulte [Personalizando RCWs (Runtime Callable Wrappers)](/previous-versions/dotnet/netframework-4.0/e753eftz(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="09c9e-196">For details about how to modify MSIL code, see [Customizing Runtime Callable Wrappers](/previous-versions/dotnet/netframework-4.0/e753eftz(v=vs.100)).</span></span> <span data-ttu-id="09c9e-197">Para indicar o número de elementos na matriz, aplique o tipo <xref:System.Runtime.InteropServices.MarshalAsAttribute> ao parâmetro de matriz da definição de método gerenciado de uma das seguintes maneiras:</span><span class="sxs-lookup"><span data-stu-id="09c9e-197">To indicate the number of elements in the array, apply the <xref:System.Runtime.InteropServices.MarshalAsAttribute> type to the array parameter of the managed method definition in one of the following ways:</span></span>  
  
- <span data-ttu-id="09c9e-198">Identifique outro parâmetro que contém o número de elementos na matriz.</span><span class="sxs-lookup"><span data-stu-id="09c9e-198">Identify another parameter that contains the number of elements in the array.</span></span> <span data-ttu-id="09c9e-199">Os parâmetros são identificados por posição, começando com o primeiro parâmetro como o número 0.</span><span class="sxs-lookup"><span data-stu-id="09c9e-199">The parameters are identified by position, starting with the first parameter as number 0.</span></span>
  
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
  
- <span data-ttu-id="09c9e-200">Defina o tamanho da matriz como uma constante.</span><span class="sxs-lookup"><span data-stu-id="09c9e-200">Define the size of the array as a constant.</span></span> <span data-ttu-id="09c9e-201">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="09c9e-201">For example:</span></span>  
  
    ```vb  
    Sub [New](\<MarshalAs(UnmanagedType.LPArray, SizeConst:=128)> _  
       ar() As Integer)  
    ```  
  
    ```csharp  
    void New(  
       [MarshalAs(UnmanagedType.LPArray, SizeConst=128)] int[] ar );  
    ```  
  
 <span data-ttu-id="09c9e-202">Ao realizar marshaling de matrizes de código não gerenciado para código gerenciado, o marshaler verifica o **MarshalAsAttribute** associado ao parâmetro para determinar o tamanho da matriz.</span><span class="sxs-lookup"><span data-stu-id="09c9e-202">When marshaling arrays from unmanaged code to managed code, the marshaler checks the **MarshalAsAttribute** associated with the parameter to determine the array size.</span></span> <span data-ttu-id="09c9e-203">Se o tamanho da matriz não for especificado, somente um elemento terá o marshaling realizado.</span><span class="sxs-lookup"><span data-stu-id="09c9e-203">If the array size is not specified, only one element is marshaled.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="09c9e-204">O **MarshalAsAttribute** não tem nenhum efeito no marshaling de matrizes gerenciadas para código não gerenciado.</span><span class="sxs-lookup"><span data-stu-id="09c9e-204">The **MarshalAsAttribute** has no effect on marshaling managed arrays to unmanaged code.</span></span> <span data-ttu-id="09c9e-205">Nessa direção, o tamanho da matriz é determinado pelo exame.</span><span class="sxs-lookup"><span data-stu-id="09c9e-205">In that direction, the array size is determined by examination.</span></span> <span data-ttu-id="09c9e-206">Não há nenhuma maneira de realizar marshaling de um subconjunto de uma matriz gerenciada.</span><span class="sxs-lookup"><span data-stu-id="09c9e-206">There is no way to marshal a subset of a managed array.</span></span>  
  
 <span data-ttu-id="09c9e-207">O marshaler de interoperabilidade usa os métodos **CoTaskMemAlloc** e **CoTaskMemFree** para alocar e recuperar a memória.</span><span class="sxs-lookup"><span data-stu-id="09c9e-207">The interop marshaler uses the **CoTaskMemAlloc** and **CoTaskMemFree** methods to allocate and retrieve memory.</span></span> <span data-ttu-id="09c9e-208">A alocação de memória executada pelo código não gerenciado também deve usar esses métodos.</span><span class="sxs-lookup"><span data-stu-id="09c9e-208">Memory allocation performed by unmanaged code must also use these methods.</span></span>  
  
## <a name="passing-arrays-to-com"></a><span data-ttu-id="09c9e-209">Passando matrizes para o COM</span><span class="sxs-lookup"><span data-stu-id="09c9e-209">Passing Arrays to COM</span></span>  
 <span data-ttu-id="09c9e-210">Todos os tipos de matriz gerenciada podem ser passados para um código não gerenciado de um código gerenciado.</span><span class="sxs-lookup"><span data-stu-id="09c9e-210">All managed array types can be passed to unmanaged code from managed code.</span></span> <span data-ttu-id="09c9e-211">Dependendo do tipo gerenciado e dos atributos aplicados a ele, a matriz pode ser acessada como uma matriz segura ou uma matriz C-style, conforme mostrado na tabela a seguir.</span><span class="sxs-lookup"><span data-stu-id="09c9e-211">Depending on the managed type and the attributes applied to it, the array can be accessed as a safe array or a C-style array, as shown in the following table.</span></span>  
  
|<span data-ttu-id="09c9e-212">Tipo de matriz gerenciada</span><span class="sxs-lookup"><span data-stu-id="09c9e-212">Managed array type</span></span>|<span data-ttu-id="09c9e-213">Exportado como</span><span class="sxs-lookup"><span data-stu-id="09c9e-213">Exported as</span></span>|  
|------------------------|-----------------|  
|<span data-ttu-id="09c9e-214">**ELEMENT_TYPE_SZARRAY\*\*\*\*\<** *type* **>**</span><span class="sxs-lookup"><span data-stu-id="09c9e-214">**ELEMENT_TYPE_SZARRAY** **\<** *type* **>**</span></span>|<span data-ttu-id="09c9e-215"><xref:System.Runtime.InteropServices.UnmanagedType> **.SafeArray(** *type* **)**</span><span class="sxs-lookup"><span data-stu-id="09c9e-215"><xref:System.Runtime.InteropServices.UnmanagedType> **.SafeArray(** *type* **)**</span></span><br /><br /> <span data-ttu-id="09c9e-216">**UnmanagedType.LPArray**</span><span class="sxs-lookup"><span data-stu-id="09c9e-216">**UnmanagedType.LPArray**</span></span><br /><br /> <span data-ttu-id="09c9e-217">O tipo é fornecido na assinatura.</span><span class="sxs-lookup"><span data-stu-id="09c9e-217">Type is provided in the signature.</span></span> <span data-ttu-id="09c9e-218">A classificação é sempre 1 e o limite inferior é sempre 0.</span><span class="sxs-lookup"><span data-stu-id="09c9e-218">Rank is always 1, lower bound is always 0.</span></span> <span data-ttu-id="09c9e-219">O tamanho é sempre conhecido em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="09c9e-219">Size is always known at run time.</span></span>|  
|<span data-ttu-id="09c9e-220">**ELEMENT_TYPE_ARRAY** **\<** *type* **>** **\<** *rank* **>**[**\<** *bounds* **>**]</span><span class="sxs-lookup"><span data-stu-id="09c9e-220">**ELEMENT_TYPE_ARRAY** **\<** *type* **>** **\<** *rank* **>**[**\<** *bounds* **>**]</span></span>|<span data-ttu-id="09c9e-221">**UnmanagedType.SafeArray(** *type* **)**</span><span class="sxs-lookup"><span data-stu-id="09c9e-221">**UnmanagedType.SafeArray(** *type* **)**</span></span><br /><br /> <span data-ttu-id="09c9e-222">**UnmanagedType.LPArray**</span><span class="sxs-lookup"><span data-stu-id="09c9e-222">**UnmanagedType.LPArray**</span></span><br /><br /> <span data-ttu-id="09c9e-223">O tipo, a classificação e os limites são fornecidos na assinatura.</span><span class="sxs-lookup"><span data-stu-id="09c9e-223">Type, rank, bounds are provided in the signature.</span></span> <span data-ttu-id="09c9e-224">O tamanho é sempre conhecido em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="09c9e-224">Size is always known at run time.</span></span>|  
|<span data-ttu-id="09c9e-225">**ELEMENT_TYPE_CLASS\*\*\*\*\<**<xref:System.Array?displayProperty=nameWithType>**>\*\*</span><span class="sxs-lookup"><span data-stu-id="09c9e-225">**ELEMENT_TYPE_CLASS** **\<**<xref:System.Array?displayProperty=nameWithType>**>\*\*</span></span>|<span data-ttu-id="09c9e-226">**UT_Interface**</span><span class="sxs-lookup"><span data-stu-id="09c9e-226">**UT_Interface**</span></span><br /><br /> <span data-ttu-id="09c9e-227">**UnmanagedType.SafeArray(** *type* **)**</span><span class="sxs-lookup"><span data-stu-id="09c9e-227">**UnmanagedType.SafeArray(** *type* **)**</span></span><br /><br /> <span data-ttu-id="09c9e-228">O tipo, a classificação, os limites e o tamanho são sempre conhecidos em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="09c9e-228">Type, rank, bounds, and size are always known at run time.</span></span>|  
  
 <span data-ttu-id="09c9e-229">Há uma limitação na Automação OLE relativa a matrizes de estruturas que contêm LPSTR ou LPWSTR.</span><span class="sxs-lookup"><span data-stu-id="09c9e-229">There is a limitation in OLE Automation relating to arrays of structures that contain LPSTR or LPWSTR.</span></span>  <span data-ttu-id="09c9e-230">Portanto, os campos **String** precisam ter o marshaling realizado como **UnmanagedType.BSTR**.</span><span class="sxs-lookup"><span data-stu-id="09c9e-230">Therefore, **String** fields have to be marshaled as **UnmanagedType.BSTR**.</span></span> <span data-ttu-id="09c9e-231">Caso contrário, uma exceção será gerada.</span><span class="sxs-lookup"><span data-stu-id="09c9e-231">Otherwise, an exception will be thrown.</span></span>  
  
### <a name="element_type_szarray"></a><span data-ttu-id="09c9e-232">ELEMENT_TYPE_SZARRAY</span><span class="sxs-lookup"><span data-stu-id="09c9e-232">ELEMENT_TYPE_SZARRAY</span></span>  
 <span data-ttu-id="09c9e-233">Quando um método que contém um parâmetro **ELEMENT_TYPE_SZARRAY** (matriz unidimensional) é exportado de um assembly .NET para uma biblioteca de tipos, o parâmetro de matriz é convertido em uma **SAFEARRAY** de determinado tipo.</span><span class="sxs-lookup"><span data-stu-id="09c9e-233">When a method containing an **ELEMENT_TYPE_SZARRAY** parameter (one-dimensional array) is exported from a .NET assembly to a type library, the array parameter is converted to a **SAFEARRAY** of a given type.</span></span> <span data-ttu-id="09c9e-234">As mesmas regras de conversão se aplicam a tipos de elemento da matriz.</span><span class="sxs-lookup"><span data-stu-id="09c9e-234">The same conversion rules apply to the array element types.</span></span> <span data-ttu-id="09c9e-235">O conteúdo da matriz gerenciada é copiado automaticamente da memória gerenciada para a **SAFEARRAY**.</span><span class="sxs-lookup"><span data-stu-id="09c9e-235">The contents of the managed array are automatically copied from managed memory into the **SAFEARRAY**.</span></span> <span data-ttu-id="09c9e-236">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="09c9e-236">For example:</span></span>  
  
#### <a name="managed-signature"></a><span data-ttu-id="09c9e-237">Assinatura gerenciada</span><span class="sxs-lookup"><span data-stu-id="09c9e-237">Managed signature</span></span>  
  
```vb  
Sub [New](ar() As Long)  
Sub [New](ar() As String)  
```  
  
```csharp  
void New(long[] ar );  
void New(String[] ar );  
```  
  
#### <a name="unmanaged-signature"></a><span data-ttu-id="09c9e-238">Assinatura não gerenciada</span><span class="sxs-lookup"><span data-stu-id="09c9e-238">Unmanaged signature</span></span>  
  
```cpp
HRESULT New([in] SAFEARRAY( long ) ar);
HRESULT New([in] SAFEARRAY( BSTR ) ar);  
```  
  
 <span data-ttu-id="09c9e-239">A classificação de matrizes seguras é sempre 1 e o limite inferior é sempre 0.</span><span class="sxs-lookup"><span data-stu-id="09c9e-239">The rank of the safe arrays is always 1 and the lower bound is always 0.</span></span> <span data-ttu-id="09c9e-240">O tamanho é determinado em tempo de execução pelo tamanho da matriz gerenciada que está sendo passada.</span><span class="sxs-lookup"><span data-stu-id="09c9e-240">The size is determined at run time by the size of the managed array being passed.</span></span>  
  
 <span data-ttu-id="09c9e-241">A matriz também pode ter o marshaling realizado como uma matriz C-style com o uso do atributo <xref:System.Runtime.InteropServices.MarshalAsAttribute>.</span><span class="sxs-lookup"><span data-stu-id="09c9e-241">The array can also be marshaled as a C-style array by using the <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribute.</span></span> <span data-ttu-id="09c9e-242">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="09c9e-242">For example:</span></span>  
  
#### <a name="managed-signature"></a><span data-ttu-id="09c9e-243">Assinatura gerenciada</span><span class="sxs-lookup"><span data-stu-id="09c9e-243">Managed signature</span></span>  
  
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
  
#### <a name="unmanaged-signature"></a><span data-ttu-id="09c9e-244">Assinatura não gerenciada</span><span class="sxs-lookup"><span data-stu-id="09c9e-244">Unmanaged signature</span></span>  
  
```cpp
HRESULT New(long ar[]);
HRESULT New(BSTR ar[]);
HRESULT New(LPStr ar[]);  
```  
  
 <span data-ttu-id="09c9e-245">Embora o marshaler tenha as informações de tamanho necessárias para realizar marshaling da matriz, o tamanho da matriz geralmente é passado como um argumento separado para transmitir o tamanho para o receptor.</span><span class="sxs-lookup"><span data-stu-id="09c9e-245">Although the marshaler has the length information needed to marshal the array, the array length is usually passed as a separate argument to convey the length to the callee.</span></span>  
  
### <a name="element_type_array"></a><span data-ttu-id="09c9e-246">ELEMENT_TYPE_ARRAY</span><span class="sxs-lookup"><span data-stu-id="09c9e-246">ELEMENT_TYPE_ARRAY</span></span>  
 <span data-ttu-id="09c9e-247">Quando um método que contém um parâmetro **ELEMENT_TYPE_ARRAY** é exportado de um assembly .NET para uma biblioteca de tipos, o parâmetro de matriz é convertido em uma **SAFEARRAY** de determinado tipo.</span><span class="sxs-lookup"><span data-stu-id="09c9e-247">When a method containing an **ELEMENT_TYPE_ARRAY** parameter is exported from a .NET assembly to a type library, the array parameter is converted to a **SAFEARRAY** of a given type.</span></span> <span data-ttu-id="09c9e-248">O conteúdo da matriz gerenciada é copiado automaticamente da memória gerenciada para a **SAFEARRAY**.</span><span class="sxs-lookup"><span data-stu-id="09c9e-248">The contents of the managed array are automatically copied from managed memory into the **SAFEARRAY**.</span></span> <span data-ttu-id="09c9e-249">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="09c9e-249">For example:</span></span>  
  
#### <a name="managed-signature"></a><span data-ttu-id="09c9e-250">Assinatura gerenciada</span><span class="sxs-lookup"><span data-stu-id="09c9e-250">Managed signature</span></span>  
  
```vb  
Sub [New](ar(,) As Long)  
Sub [New](ar(,) As String)  
```  
  
```csharp  
void New( long [,] ar );  
void New( String [,] ar );  
```  
  
#### <a name="unmanaged-signature"></a><span data-ttu-id="09c9e-251">Assinatura não gerenciada</span><span class="sxs-lookup"><span data-stu-id="09c9e-251">Unmanaged signature</span></span>  
  
```cpp
HRESULT New([in] SAFEARRAY( long ) ar);
HRESULT New([in] SAFEARRAY( BSTR ) ar);  
```  
  
 <span data-ttu-id="09c9e-252">A classificação, o tamanho e os limites das matrizes seguras são determinados em tempo de execução pelas características da matriz gerenciada.</span><span class="sxs-lookup"><span data-stu-id="09c9e-252">The rank, size, and bounds of the safe arrays are determined at run time by the characteristics of the managed array.</span></span>  
  
 <span data-ttu-id="09c9e-253">A matriz também pode ter o marshaling realizado como uma matriz C-style com a aplicação do atributo <xref:System.Runtime.InteropServices.MarshalAsAttribute>.</span><span class="sxs-lookup"><span data-stu-id="09c9e-253">The array can also be marshaled as a C-style array by applying the <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribute.</span></span> <span data-ttu-id="09c9e-254">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="09c9e-254">For example:</span></span>  
  
#### <a name="managed-signature"></a><span data-ttu-id="09c9e-255">Assinatura gerenciada</span><span class="sxs-lookup"><span data-stu-id="09c9e-255">Managed signature</span></span>  
  
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
  
#### <a name="unmanaged-signature"></a><span data-ttu-id="09c9e-256">Assinatura não gerenciada</span><span class="sxs-lookup"><span data-stu-id="09c9e-256">Unmanaged signature</span></span>  
  
```cpp
HRESULT New(long ar[]);
HRESULT New(LPStr ar[]);  
```  
  
 <span data-ttu-id="09c9e-257">Não é possível realizar marshaling de matrizes aninhadas.</span><span class="sxs-lookup"><span data-stu-id="09c9e-257">Nested arrays cannot be marshaled.</span></span> <span data-ttu-id="09c9e-258">Por exemplo, a assinatura a seguir gera um erro quando exportada com o [Exportador da Biblioteca de Tipos (Tlbexp.exe)](../tools/tlbexp-exe-type-library-exporter.md).</span><span class="sxs-lookup"><span data-stu-id="09c9e-258">For example, the following signature generates an error when exported with the [Type Library Exporter (Tlbexp.exe)](../tools/tlbexp-exe-type-library-exporter.md).</span></span>  
  
#### <a name="managed-signature"></a><span data-ttu-id="09c9e-259">Assinatura gerenciada</span><span class="sxs-lookup"><span data-stu-id="09c9e-259">Managed signature</span></span>  
  
```vb  
Sub [New](ar()()() As Long)  
```  
  
```csharp  
void New(long [][][] ar );  
```  
  
### <a name="element_type_class-systemarray"></a><span data-ttu-id="09c9e-260">ELEMENT_TYPE_CLASS \<System.Array></span><span class="sxs-lookup"><span data-stu-id="09c9e-260">ELEMENT_TYPE_CLASS \<System.Array></span></span>  
 <span data-ttu-id="09c9e-261">Quando um método que contém um parâmetro <xref:System.Array?displayProperty=nameWithType> é exportado de um assembly .NET para uma biblioteca de tipos, o parâmetro da matriz é convertido em uma interface **_Array**.</span><span class="sxs-lookup"><span data-stu-id="09c9e-261">When a method containing a <xref:System.Array?displayProperty=nameWithType> parameter is exported from a .NET assembly to a type library, the array parameter is converted to an **_Array** interface.</span></span> <span data-ttu-id="09c9e-262">O conteúdo da matriz gerenciada é acessível somente por meio dos métodos e das propriedades da interface **_Array**.</span><span class="sxs-lookup"><span data-stu-id="09c9e-262">The contents of the managed array are accessible only through the methods and properties of the **_Array** interface.</span></span> <span data-ttu-id="09c9e-263">**System.Array** também pode ter o marshaling realizado como uma **SAFEARRAY** usando o atributo <xref:System.Runtime.InteropServices.MarshalAsAttribute>.</span><span class="sxs-lookup"><span data-stu-id="09c9e-263">**System.Array** can also be marshaled as a **SAFEARRAY** by using the <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribute.</span></span> <span data-ttu-id="09c9e-264">Ao ter o marshaling realizado como uma matriz segura, os elementos da matriz têm o marshaling realizado como variantes.</span><span class="sxs-lookup"><span data-stu-id="09c9e-264">When marshaled as a safe array, the array elements are marshaled as variants.</span></span> <span data-ttu-id="09c9e-265">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="09c9e-265">For example:</span></span>  
  
#### <a name="managed-signature"></a><span data-ttu-id="09c9e-266">Assinatura gerenciada</span><span class="sxs-lookup"><span data-stu-id="09c9e-266">Managed signature</span></span>  
  
```vb  
Sub New1( ar As System.Array )  
Sub New2( <MarshalAs(UnmanagedType.Safe array)> ar As System.Array )  
```  
  
```csharp  
void New1( System.Array ar );  
void New2( [MarshalAs(UnmanagedType.Safe array)] System.Array ar );  
```  
  
#### <a name="unmanaged-signature"></a><span data-ttu-id="09c9e-267">Assinatura não gerenciada</span><span class="sxs-lookup"><span data-stu-id="09c9e-267">Unmanaged signature</span></span>  
  
```cpp
HRESULT New([in] _Array *ar);
HRESULT New([in] SAFEARRAY(VARIANT) ar);  
```  
  
### <a name="arrays-within-structures"></a><span data-ttu-id="09c9e-268">Matrizes em estruturas</span><span class="sxs-lookup"><span data-stu-id="09c9e-268">Arrays within Structures</span></span>  
 <span data-ttu-id="09c9e-269">Estruturas não gerenciadas podem conter matrizes inseridas.</span><span class="sxs-lookup"><span data-stu-id="09c9e-269">Unmanaged structures can contain embedded arrays.</span></span> <span data-ttu-id="09c9e-270">Por padrão, esses campos de matriz inseridos têm o marshaling realizado como uma SAFEARRAY.</span><span class="sxs-lookup"><span data-stu-id="09c9e-270">By default, these embedded array fields are marshaled as a SAFEARRAY.</span></span> <span data-ttu-id="09c9e-271">No exemplo a seguir, `s1` é uma matriz inserida que é alocada diretamente na própria estrutura.</span><span class="sxs-lookup"><span data-stu-id="09c9e-271">In the following example, `s1` is an embedded array that is allocated directly within the structure itself.</span></span>  
  
#### <a name="unmanaged-representation"></a><span data-ttu-id="09c9e-272">Representação não gerenciada</span><span class="sxs-lookup"><span data-stu-id="09c9e-272">Unmanaged representation</span></span>  
  
```cpp
struct MyStruct {  
    short s1[128];  
}  
```  
  
 <span data-ttu-id="09c9e-273">Matrizes podem ter o marshaling realizado como <xref:System.Runtime.InteropServices.UnmanagedType>, o que exige a definição do campo <xref:System.Runtime.InteropServices.MarshalAsAttribute>.</span><span class="sxs-lookup"><span data-stu-id="09c9e-273">Arrays can be marshaled as <xref:System.Runtime.InteropServices.UnmanagedType>, which requires you to set the <xref:System.Runtime.InteropServices.MarshalAsAttribute> field.</span></span> <span data-ttu-id="09c9e-274">O tamanho pode ser definido somente como uma constante.</span><span class="sxs-lookup"><span data-stu-id="09c9e-274">The size can be set only as a constant.</span></span> <span data-ttu-id="09c9e-275">O código a seguir mostra a definição gerenciada correspondente de `MyStruct`.</span><span class="sxs-lookup"><span data-stu-id="09c9e-275">The following code shows the corresponding managed definition of `MyStruct`.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="09c9e-276">Confira também</span><span class="sxs-lookup"><span data-stu-id="09c9e-276">See also</span></span>

- [<span data-ttu-id="09c9e-277">Comportamento de marshaling padrão</span><span class="sxs-lookup"><span data-stu-id="09c9e-277">Default Marshaling Behavior</span></span>](default-marshaling-behavior.md)
- [<span data-ttu-id="09c9e-278">Tipos blittable e não blittable</span><span class="sxs-lookup"><span data-stu-id="09c9e-278">Blittable and Non-Blittable Types</span></span>](blittable-and-non-blittable-types.md)
- <span data-ttu-id="09c9e-279">[Atributos direcionais](/previous-versions/dotnet/netframework-4.0/77e6taeh(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="09c9e-279">[Directional Attributes](/previous-versions/dotnet/netframework-4.0/77e6taeh(v=vs.100))</span></span>
- [<span data-ttu-id="09c9e-280">Copiando e fixando</span><span class="sxs-lookup"><span data-stu-id="09c9e-280">Copying and Pinning</span></span>](copying-and-pinning.md)
