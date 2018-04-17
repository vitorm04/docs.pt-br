---
title: Marshaling padrão para objetos
ms.date: 03/30/2017
ms.prod: .net-framework
ms.technology:
- dotnet-clr
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- objects, interop marshaling
- interop marshaling, objects
ms.assetid: c2ef0284-b061-4e12-b6d3-6a502b9cc558
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 6980db381322d354cace38709586e50681ae0a7e
ms.sourcegitcommit: 9a4fe1a1c37b26532654b4bbe22d702237950009
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
---
# <a name="default-marshaling-for-objects"></a><span data-ttu-id="3ed00-102">Marshaling padrão para objetos</span><span class="sxs-lookup"><span data-stu-id="3ed00-102">Default Marshaling for Objects</span></span>
<span data-ttu-id="3ed00-103">Os parâmetros e os campos tipados como <xref:System.Object?displayProperty=nameWithType> podem ser expostos para um código não gerenciado como um dos seguintes tipos:</span><span class="sxs-lookup"><span data-stu-id="3ed00-103">Parameters and fields typed as <xref:System.Object?displayProperty=nameWithType> can be exposed to unmanaged code as one of the following types:</span></span>  
  
-   <span data-ttu-id="3ed00-104">Uma variante quando o objeto é um parâmetro.</span><span class="sxs-lookup"><span data-stu-id="3ed00-104">A variant when the object is a parameter.</span></span>  
  
-   <span data-ttu-id="3ed00-105">Uma interface quando o objeto é um campo de estrutura.</span><span class="sxs-lookup"><span data-stu-id="3ed00-105">An interface when the object is a structure field.</span></span>  
  
 <span data-ttu-id="3ed00-106">Somente a interoperabilidade COM dá suporte ao marshaling de tipos de objeto.</span><span class="sxs-lookup"><span data-stu-id="3ed00-106">Only COM interop supports marshaling for object types.</span></span> <span data-ttu-id="3ed00-107">O comportamento padrão é realizar marshaling de objetos para variantes COM.</span><span class="sxs-lookup"><span data-stu-id="3ed00-107">The default behavior is to marshal objects to COM variants.</span></span> <span data-ttu-id="3ed00-108">Essas regras se aplicam somente ao tipo **Object** e não se aplicam a objetos fortemente tipados derivados da classe **Object**.</span><span class="sxs-lookup"><span data-stu-id="3ed00-108">These rules apply only to the type **Object** and do not apply to strongly typed objects that derive from the **Object** class.</span></span>  
  
 <span data-ttu-id="3ed00-109">Este tópico fornece as seguintes informações adicionais sobre o marshaling de tipos de objeto:</span><span class="sxs-lookup"><span data-stu-id="3ed00-109">This topic provides the following additional information about marshaling object types:</span></span>  
  
-   [<span data-ttu-id="3ed00-110">Opções de marshaling</span><span class="sxs-lookup"><span data-stu-id="3ed00-110">Marshaling Options</span></span>](#cpcondefaultmarshalingforobjectsanchor7)  
  
-   [<span data-ttu-id="3ed00-111">Realizando marshaling de objeto para interface</span><span class="sxs-lookup"><span data-stu-id="3ed00-111">Marshaling Object to Interface</span></span>](#cpcondefaultmarshalingforobjectsanchor2)  
  
-   [<span data-ttu-id="3ed00-112">Realizando marshaling de objeto para variante</span><span class="sxs-lookup"><span data-stu-id="3ed00-112">Marshaling Object to Variant</span></span>](#cpcondefaultmarshalingforobjectsanchor3)  
  
-   [<span data-ttu-id="3ed00-113">Realizando marshaling de variante para objeto</span><span class="sxs-lookup"><span data-stu-id="3ed00-113">Marshaling Variant to Object</span></span>](#cpcondefaultmarshalingforobjectsanchor4)  
  
-   [<span data-ttu-id="3ed00-114">Realizando marshaling de variantes de ByRef</span><span class="sxs-lookup"><span data-stu-id="3ed00-114">Marshaling ByRef Variants</span></span>](#cpcondefaultmarshalingforobjectsanchor6)  
  
<a name="cpcondefaultmarshalingforobjectsanchor7"></a>   
## <a name="marshaling-options"></a><span data-ttu-id="3ed00-115">Opções de marshaling</span><span class="sxs-lookup"><span data-stu-id="3ed00-115">Marshaling Options</span></span>  
 <span data-ttu-id="3ed00-116">A tabela a seguir mostra as opções de marshaling para o tipo de dados **Object**.</span><span class="sxs-lookup"><span data-stu-id="3ed00-116">The following table shows the marshaling options for the **Object** data type.</span></span> <span data-ttu-id="3ed00-117">O atributo <xref:System.Runtime.InteropServices.MarshalAsAttribute> fornece vários valores de enumeração <xref:System.Runtime.InteropServices.UnmanagedType> para realizar marshaling de objetos.</span><span class="sxs-lookup"><span data-stu-id="3ed00-117">The <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribute provides several <xref:System.Runtime.InteropServices.UnmanagedType> enumeration values to marshal objects.</span></span>  
  
|<span data-ttu-id="3ed00-118">Tipo de enumeração</span><span class="sxs-lookup"><span data-stu-id="3ed00-118">Enumeration type</span></span>|<span data-ttu-id="3ed00-119">Descrição do formato não gerenciado</span><span class="sxs-lookup"><span data-stu-id="3ed00-119">Description of unmanaged format</span></span>|  
|----------------------|-------------------------------------|  
|<span data-ttu-id="3ed00-120">**UnmanagedType.Struct**</span><span class="sxs-lookup"><span data-stu-id="3ed00-120">**UnmanagedType.Struct**</span></span><br /><br /> <span data-ttu-id="3ed00-121">(padrão para parâmetros)</span><span class="sxs-lookup"><span data-stu-id="3ed00-121">(default for parameters)</span></span>|<span data-ttu-id="3ed00-122">Uma variante de estilo COM.</span><span class="sxs-lookup"><span data-stu-id="3ed00-122">A COM-style variant.</span></span>|  
|<span data-ttu-id="3ed00-123">**UnmanagedType.Interface**</span><span class="sxs-lookup"><span data-stu-id="3ed00-123">**UnmanagedType.Interface**</span></span>|<span data-ttu-id="3ed00-124">Uma interface **IDispatch**, se possível; caso contrário, uma interface **IUnknown**.</span><span class="sxs-lookup"><span data-stu-id="3ed00-124">An **IDispatch** interface, if possible; otherwise, an **IUnknown** interface.</span></span>|  
|<span data-ttu-id="3ed00-125">**UnmanagedType.IUnknown**</span><span class="sxs-lookup"><span data-stu-id="3ed00-125">**UnmanagedType.IUnknown**</span></span><br /><br /> <span data-ttu-id="3ed00-126">(padrão para campos)</span><span class="sxs-lookup"><span data-stu-id="3ed00-126">(default for fields)</span></span>|<span data-ttu-id="3ed00-127">Uma interface **IUnknown**.</span><span class="sxs-lookup"><span data-stu-id="3ed00-127">An **IUnknown** interface.</span></span>|  
|<span data-ttu-id="3ed00-128">**UnmanagedType.IDispatch**</span><span class="sxs-lookup"><span data-stu-id="3ed00-128">**UnmanagedType.IDispatch**</span></span>|<span data-ttu-id="3ed00-129">Uma interface **IDispatch**.</span><span class="sxs-lookup"><span data-stu-id="3ed00-129">An **IDispatch** interface.</span></span>|  
  
 <span data-ttu-id="3ed00-130">O exemplo a seguir mostra a definição de interface gerenciada para `MarshalObject`.</span><span class="sxs-lookup"><span data-stu-id="3ed00-130">The following example shows the managed interface definition for `MarshalObject`.</span></span>  
  
```vb  
Interface MarshalObject  
   Sub SetVariant(o As Object)  
   Sub SetVariantRef(ByRef o As Object)  
   Function GetVariant() As Object  
  
   Sub SetIDispatch( <MarshalAs(UnmanagedType.IDispatch)> o As Object)  
   Sub SetIDispatchRef(ByRef <MarshalAs(UnmanagedType.IDispatch)> o _  
      As Object)  
   Function GetIDispatch() As <MarshalAs(UnmanagedType.IDispatch)> Object  
   Sub SetIUnknown( <MarshalAs(UnmanagedType.IUnknown)> o As Object)  
   Sub SetIUnknownRef(ByRef <MarshalAs(UnmanagedType.IUnknown)> o _  
      As Object)  
   Function GetIUnknown() As <MarshalAs(UnmanagedType.IUnknown)> Object  
End Interface  
```  
  
```csharp  
interface MarshalObject {  
   void SetVariant(Object o);  
   void SetVariantRef(ref Object o);  
   Object GetVariant();  
  
   void SetIDispatch ([MarshalAs(UnmanagedType.IDispatch)]Object o);  
   void SetIDispatchRef([MarshalAs(UnmanagedType.IDispatch)]ref Object o);  
   [MarshalAs(UnmanagedType.IDispatch)] Object GetIDispatch();  
   void SetIUnknown ([MarshalAs(UnmanagedType.IUnknown)]Object o);  
   void SetIUnknownRef([MarshalAs(UnmanagedType.IUnknown)]ref Object o);  
   [MarshalAs(UnmanagedType.IUnknown)] Object GetIUnknown();  
}  
```  
  
 <span data-ttu-id="3ed00-131">O código a seguir exporta a interface `MarshalObject` para uma biblioteca de tipos.</span><span class="sxs-lookup"><span data-stu-id="3ed00-131">The following code exports the `MarshalObject` interface to a type library.</span></span>  
  
```  
interface MarshalObject {  
   HRESULT SetVariant([in] VARIANT o);  
   HRESULT SetVariantRef([in,out] VARIANT *o);  
   HRESULT GetVariant([out,retval] VARIANT *o)   
   HRESULT SetIDispatch([in] IDispatch *o);  
   HRESULT SetIDispatchRef([in,out] IDispatch **o);  
   HRESULT GetIDispatch([out,retval] IDispatch **o)   
   HRESULT SetIUnknown([in] IUnknown *o);  
   HRESULT SetIUnknownRef([in,out] IUnknown **o);  
   HRESULT GetIUnknown([out,retval] IUnknown **o)   
}  
```  
  
> [!NOTE]
>  <span data-ttu-id="3ed00-132">O marshaler de interoperabilidade libera automaticamente qualquer objeto alocado dentro na variante após a chamada.</span><span class="sxs-lookup"><span data-stu-id="3ed00-132">The interop marshaler automatically frees any allocated object inside the variant after the call.</span></span>  
  
 <span data-ttu-id="3ed00-133">O exemplo a seguir mostra um tipo de valor formatado.</span><span class="sxs-lookup"><span data-stu-id="3ed00-133">The following example shows a formatted value type.</span></span>  
  
```vb  
Public Structure ObjectHolder  
   Dim o1 As Object  
   <MarshalAs(UnmanagedType.IDispatch)> Public o2 As Object  
End Structure  
```  
  
```csharp  
public struct ObjectHolder {  
   Object o1;  
   [MarshalAs(UnmanagedType.IDispatch)]public Object o2;  
}  
```  
  
 <span data-ttu-id="3ed00-134">O código a seguir exporta o tipo formatado para uma biblioteca de tipos.</span><span class="sxs-lookup"><span data-stu-id="3ed00-134">The following code exports the formatted type to a type library.</span></span>  
  
```  
struct ObjectHolder {  
   VARIANT o1;  
   IDispatch *o2;  
}  
```  
  
<a name="cpcondefaultmarshalingforobjectsanchor2"></a>   
## <a name="marshaling-object-to-interface"></a><span data-ttu-id="3ed00-135">Realizando marshaling de objeto para interface</span><span class="sxs-lookup"><span data-stu-id="3ed00-135">Marshaling Object to Interface</span></span>  
 <span data-ttu-id="3ed00-136">Quando um objeto é exposto para o COM como uma interface, essa interface é a interface de classe do tipo gerenciado <xref:System.Object> (a interface **_Object**).</span><span class="sxs-lookup"><span data-stu-id="3ed00-136">When an object is exposed to COM as an interface, that interface is the class interface for the managed type <xref:System.Object> (the **_Object** interface).</span></span> <span data-ttu-id="3ed00-137">Essa interface é tipada como um **IDispatch** (<xref:System.Runtime.InteropServices.UnmanagedType>) ou um **IUnknown** (**UnmanagedType.IUnknown**) na biblioteca de tipos resultante.</span><span class="sxs-lookup"><span data-stu-id="3ed00-137">This interface is typed as an **IDispatch** (<xref:System.Runtime.InteropServices.UnmanagedType>) or an **IUnknown** (**UnmanagedType.IUnknown**) in the resulting type library.</span></span> <span data-ttu-id="3ed00-138">Os clientes COM podem invocar dinamicamente os membros da classe gerenciada ou todos os membros implementados por suas classes derivadas por meio da interface **_Object**.</span><span class="sxs-lookup"><span data-stu-id="3ed00-138">COM clients can dynamically invoke the members of the managed class or any members implemented by its derived classes through the **_Object** interface.</span></span> <span data-ttu-id="3ed00-139">O cliente também pode chamar **QueryInterface** para obter qualquer outra interface implementada explicitamente pelo tipo gerenciado.</span><span class="sxs-lookup"><span data-stu-id="3ed00-139">The client can also call **QueryInterface** to obtain any other interface explicitly implemented by the managed type.</span></span>  
  
<a name="cpcondefaultmarshalingforobjectsanchor3"></a>   
## <a name="marshaling-object-to-variant"></a><span data-ttu-id="3ed00-140">Realizando marshaling de objeto para variante</span><span class="sxs-lookup"><span data-stu-id="3ed00-140">Marshaling Object to Variant</span></span>  
 <span data-ttu-id="3ed00-141">Quando um objeto tem o marshaling realizado como uma variante, o tipo de variante interno é determinado em tempo de execução, de acordo com as seguintes regras:</span><span class="sxs-lookup"><span data-stu-id="3ed00-141">When an object is marshaled to a variant, the internal variant type is determined at run time, based on the following rules:</span></span>  
  
-   <span data-ttu-id="3ed00-142">Se a referência de objeto for nula (**Nothing** no Visual Basic), o objeto terá o marshaling realizado como uma variante do tipo **VT_EMPTY**.</span><span class="sxs-lookup"><span data-stu-id="3ed00-142">If the object reference is null (**Nothing** in Visual Basic), the object is marshaled to a variant of type **VT_EMPTY**.</span></span>  
  
-   <span data-ttu-id="3ed00-143">Se o objeto for uma instância de qualquer tipo listado na tabela a seguir, o tipo de variante resultante será determinado pelas regras internas do marshaler e mostrado na tabela.</span><span class="sxs-lookup"><span data-stu-id="3ed00-143">If the object is an instance of any type listed in the following table, the resulting variant type is determined by the rules built into the marshaler and shown in the table.</span></span>  
  
-   <span data-ttu-id="3ed00-144">Outros objetos que precisam controlar explicitamente o comportamento de marshaling podem implementar a interface <xref:System.IConvertible>.</span><span class="sxs-lookup"><span data-stu-id="3ed00-144">Other objects that need to explicitly control the marshaling behavior can implement the <xref:System.IConvertible> interface.</span></span> <span data-ttu-id="3ed00-145">Nesse caso, o tipo de variante é determinado pelo código do tipo retornado do método <xref:System.IConvertible.GetTypeCode%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="3ed00-145">In that case, the variant type is determined by the type code returned from the <xref:System.IConvertible.GetTypeCode%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="3ed00-146">Caso contrário, o objeto terá o marshaling realizado como uma variante do tipo **VT_UNKNOWN**.</span><span class="sxs-lookup"><span data-stu-id="3ed00-146">Otherwise, the object is marshaled as a variant of type **VT_UNKNOWN**.</span></span>  
  
### <a name="marshaling-system-types-to-variant"></a><span data-ttu-id="3ed00-147">Realizando marshaling de tipos do sistema para variante</span><span class="sxs-lookup"><span data-stu-id="3ed00-147">Marshaling System Types to Variant</span></span>  
 <span data-ttu-id="3ed00-148">A tabela a seguir mostra os tipos de objeto gerenciados e seus tipos de variante COM correspondentes.</span><span class="sxs-lookup"><span data-stu-id="3ed00-148">The following table shows managed object types and their corresponding COM variant types.</span></span> <span data-ttu-id="3ed00-149">Esses tipos são convertidos somente quando a assinatura do método que está sendo chamado é do tipo <xref:System.Object?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="3ed00-149">These types are converted only when the signature of the method being called is of type <xref:System.Object?displayProperty=nameWithType>.</span></span>  
  
|<span data-ttu-id="3ed00-150">Tipo de objeto</span><span class="sxs-lookup"><span data-stu-id="3ed00-150">Object type</span></span>|<span data-ttu-id="3ed00-151">Tipo de variante COM</span><span class="sxs-lookup"><span data-stu-id="3ed00-151">COM variant type</span></span>|  
|-----------------|----------------------|  
|<span data-ttu-id="3ed00-152">Referência de objeto nulo (**Nothing** no Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="3ed00-152">Null object reference (**Nothing** in Visual Basic).</span></span>|<span data-ttu-id="3ed00-153">**VT_EMPTY**</span><span class="sxs-lookup"><span data-stu-id="3ed00-153">**VT_EMPTY**</span></span>|  
|<xref:System.DBNull?displayProperty=nameWithType>|<span data-ttu-id="3ed00-154">**VT_NULL**</span><span class="sxs-lookup"><span data-stu-id="3ed00-154">**VT_NULL**</span></span>|  
|<xref:System.Runtime.InteropServices.ErrorWrapper?displayProperty=nameWithType>|<span data-ttu-id="3ed00-155">**VT_ERROR**</span><span class="sxs-lookup"><span data-stu-id="3ed00-155">**VT_ERROR**</span></span>|  
|<xref:System.Reflection.Missing?displayProperty=nameWithType>|<span data-ttu-id="3ed00-156">**VT_ERROR** com **E_PARAMNOTFOUND**</span><span class="sxs-lookup"><span data-stu-id="3ed00-156">**VT_ERROR** with **E_PARAMNOTFOUND**</span></span>|  
|<xref:System.Runtime.InteropServices.DispatchWrapper?displayProperty=nameWithType>|<span data-ttu-id="3ed00-157">**VT_DISPATCH**</span><span class="sxs-lookup"><span data-stu-id="3ed00-157">**VT_DISPATCH**</span></span>|  
|<xref:System.Runtime.InteropServices.UnknownWrapper?displayProperty=nameWithType>|<span data-ttu-id="3ed00-158">**VT_UNKNOWN**</span><span class="sxs-lookup"><span data-stu-id="3ed00-158">**VT_UNKNOWN**</span></span>|  
|<xref:System.Runtime.InteropServices.CurrencyWrapper?displayProperty=nameWithType>|<span data-ttu-id="3ed00-159">**VT_CY**</span><span class="sxs-lookup"><span data-stu-id="3ed00-159">**VT_CY**</span></span>|  
|<xref:System.Boolean?displayProperty=nameWithType>|<span data-ttu-id="3ed00-160">**VT_BOOL**</span><span class="sxs-lookup"><span data-stu-id="3ed00-160">**VT_BOOL**</span></span>|  
|<xref:System.SByte?displayProperty=nameWithType>|<span data-ttu-id="3ed00-161">**VT_I1**</span><span class="sxs-lookup"><span data-stu-id="3ed00-161">**VT_I1**</span></span>|  
|<xref:System.Byte?displayProperty=nameWithType>|<span data-ttu-id="3ed00-162">**VT_UI1**</span><span class="sxs-lookup"><span data-stu-id="3ed00-162">**VT_UI1**</span></span>|  
|<xref:System.Int16?displayProperty=nameWithType>|<span data-ttu-id="3ed00-163">**VT_I2**</span><span class="sxs-lookup"><span data-stu-id="3ed00-163">**VT_I2**</span></span>|  
|<xref:System.UInt16?displayProperty=nameWithType>|<span data-ttu-id="3ed00-164">**VT_UI2**</span><span class="sxs-lookup"><span data-stu-id="3ed00-164">**VT_UI2**</span></span>|  
|<xref:System.Int32?displayProperty=nameWithType>|<span data-ttu-id="3ed00-165">**VT_I4**</span><span class="sxs-lookup"><span data-stu-id="3ed00-165">**VT_I4**</span></span>|  
|<xref:System.UInt32?displayProperty=nameWithType>|<span data-ttu-id="3ed00-166">**VT_UI4**</span><span class="sxs-lookup"><span data-stu-id="3ed00-166">**VT_UI4**</span></span>|  
|<xref:System.Int64?displayProperty=nameWithType>|<span data-ttu-id="3ed00-167">**VT_I8**</span><span class="sxs-lookup"><span data-stu-id="3ed00-167">**VT_I8**</span></span>|  
|<xref:System.UInt64?displayProperty=nameWithType>|<span data-ttu-id="3ed00-168">**VT_UI8**</span><span class="sxs-lookup"><span data-stu-id="3ed00-168">**VT_UI8**</span></span>|  
|<xref:System.Single?displayProperty=nameWithType>|<span data-ttu-id="3ed00-169">**VT_R4**</span><span class="sxs-lookup"><span data-stu-id="3ed00-169">**VT_R4**</span></span>|  
|<xref:System.Double?displayProperty=nameWithType>|<span data-ttu-id="3ed00-170">**VT_R8**</span><span class="sxs-lookup"><span data-stu-id="3ed00-170">**VT_R8**</span></span>|  
|<xref:System.Decimal?displayProperty=nameWithType>|<span data-ttu-id="3ed00-171">**VT_DECIMAL**</span><span class="sxs-lookup"><span data-stu-id="3ed00-171">**VT_DECIMAL**</span></span>|  
|<xref:System.DateTime?displayProperty=nameWithType>|<span data-ttu-id="3ed00-172">**VT_DATE**</span><span class="sxs-lookup"><span data-stu-id="3ed00-172">**VT_DATE**</span></span>|  
|<xref:System.String?displayProperty=nameWithType>|<span data-ttu-id="3ed00-173">**VT_BSTR**</span><span class="sxs-lookup"><span data-stu-id="3ed00-173">**VT_BSTR**</span></span>|  
|<xref:System.IntPtr?displayProperty=nameWithType>|<span data-ttu-id="3ed00-174">**VT_INT**</span><span class="sxs-lookup"><span data-stu-id="3ed00-174">**VT_INT**</span></span>|  
|<xref:System.UIntPtr?displayProperty=nameWithType>|<span data-ttu-id="3ed00-175">**VT_UINT**</span><span class="sxs-lookup"><span data-stu-id="3ed00-175">**VT_UINT**</span></span>|  
|<xref:System.Array?displayProperty=nameWithType>|<span data-ttu-id="3ed00-176">**VT_ARRAY**</span><span class="sxs-lookup"><span data-stu-id="3ed00-176">**VT_ARRAY**</span></span>|  
  
 <span data-ttu-id="3ed00-177">Usando a interface `MarshalObject` definida no exemplo anterior, o exemplo de código a seguir demonstra como passar vários tipos de variantes para um servidor COM.</span><span class="sxs-lookup"><span data-stu-id="3ed00-177">Using the `MarshalObject` interface defined in the previous example, the following code example demonstrates how to pass various types of variants to a COM server.</span></span>  
  
```vb  
Dim mo As New MarshalObject()  
mo.SetVariant(Nothing)         ' Marshal as variant of type VT_EMPTY.  
mo.SetVariant(System.DBNull.Value) ' Marshal as variant of type VT_NULL.  
mo.SetVariant(CInt(27))        ' Marshal as variant of type VT_I2.  
mo.SetVariant(CLng(27))        ' Marshal as variant of type VT_I4.  
mo.SetVariant(CSng(27.0))      ' Marshal as variant of type VT_R4.  
mo.SetVariant(CDbl(27.0))      ' Marshal as variant of type VT_R8.  
```  
  
```csharp  
MarshalObject mo = new MarshalObject();  
mo.SetVariant(null);            // Marshal as variant of type VT_EMPTY.  
mo.SetVariant(System.DBNull.Value); // Marshal as variant of type VT_NULL.  
mo.SetVariant((int)27);          // Marshal as variant of type VT_I2.  
mo.SetVariant((long)27);          // Marshal as variant of type VT_I4.  
mo.SetVariant((single)27.0);   // Marshal as variant of type VT_R4.  
mo.SetVariant((double)27.0);   // Marshal as variant of type VT_R8.  
```  
  
 <span data-ttu-id="3ed00-178">Tipos COM que não têm tipos gerenciados correspondentes podem ter o marshaling realizado usando classes wrapper como <xref:System.Runtime.InteropServices.ErrorWrapper>, <xref:System.Runtime.InteropServices.DispatchWrapper>, <xref:System.Runtime.InteropServices.UnknownWrapper> e <xref:System.Runtime.InteropServices.CurrencyWrapper>.</span><span class="sxs-lookup"><span data-stu-id="3ed00-178">COM types that do not have corresponding managed types can be marshaled using wrapper classes such as <xref:System.Runtime.InteropServices.ErrorWrapper>, <xref:System.Runtime.InteropServices.DispatchWrapper>, <xref:System.Runtime.InteropServices.UnknownWrapper>, and <xref:System.Runtime.InteropServices.CurrencyWrapper>.</span></span> <span data-ttu-id="3ed00-179">O exemplo de código a seguir demonstra como usar esses wrappers para passar vários tipos de variantes para um servidor COM.</span><span class="sxs-lookup"><span data-stu-id="3ed00-179">The following code example demonstrates how to use these wrappers to pass various types of variants to a COM server.</span></span>  
  
```vb  
Imports System.Runtime.InteropServices  
' Pass inew as a variant of type VT_UNKNOWN interface.  
mo.SetVariant(New UnknownWrapper(inew))  
' Pass inew as a variant of type VT_DISPATCH interface.  
mo.SetVariant(New DispatchWrapper(inew))  
' Pass a value as a variant of type VT_ERROR interface.  
mo.SetVariant(New ErrorWrapper(&H80054002))  
' Pass a value as a variant of type VT_CURRENCY interface.  
mo.SetVariant(New CurrencyWrapper(New Decimal(5.25)))  
```  
  
```csharp  
using System.Runtime.InteropServices;  
// Pass inew as a variant of type VT_UNKNOWN interface.  
mo.SetVariant(new UnknownWrapper(inew));  
// Pass inew as a variant of type VT_DISPATCH interface.  
mo.SetVariant(new DispatchWrapper(inew));  
// Pass a value as a variant of type VT_ERROR interface.  
mo.SetVariant(new ErrorWrapper(0x80054002));  
// Pass a value as a variant of type VT_CURRENCY interface.  
mo.SetVariant(new CurrencyWrapper(new Decimal(5.25)));  
```  
  
 <span data-ttu-id="3ed00-180">As classes wrapper são definidas no namespace <xref:System.Runtime.InteropServices>.</span><span class="sxs-lookup"><span data-stu-id="3ed00-180">The wrapper classes are defined in the <xref:System.Runtime.InteropServices> namespace.</span></span>  
  
### <a name="marshaling-the-iconvertible-interface-to-variant"></a><span data-ttu-id="3ed00-181">Realizando marshaling da interface IConvertible para variante</span><span class="sxs-lookup"><span data-stu-id="3ed00-181">Marshaling the IConvertible Interface to Variant</span></span>  
 <span data-ttu-id="3ed00-182">Outros tipos além daqueles listados na seção anterior podem controlar seu marshaling com a implementação da interface <xref:System.IConvertible>.</span><span class="sxs-lookup"><span data-stu-id="3ed00-182">Types other than those listed in the previous section can control how they are marshaled by implementing the <xref:System.IConvertible> interface.</span></span> <span data-ttu-id="3ed00-183">Se o objeto implementar a interface **IConvertible**, o tipo de variante COM será determinado em tempo de execução pelo valor da enumeração <xref:System.TypeCode> retornado do método <xref:System.IConvertible.GetTypeCode%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="3ed00-183">If the object implements the **IConvertible** interface, the COM variant type is determined at run time by the value of the <xref:System.TypeCode> enumeration returned from the <xref:System.IConvertible.GetTypeCode%2A?displayProperty=nameWithType> method.</span></span>  
  
 <span data-ttu-id="3ed00-184">A tabela a seguir mostra os valores possíveis para a enumeração **TypeCode** e o tipo de variante COM correspondente para cada valor.</span><span class="sxs-lookup"><span data-stu-id="3ed00-184">The following table shows the possible values for the **TypeCode** enumeration and the corresponding COM variant type for each value.</span></span>  
  
|<span data-ttu-id="3ed00-185">TypeCode</span><span class="sxs-lookup"><span data-stu-id="3ed00-185">TypeCode</span></span>|<span data-ttu-id="3ed00-186">Tipo de variante COM</span><span class="sxs-lookup"><span data-stu-id="3ed00-186">COM variant type</span></span>|  
|--------------|----------------------|  
|<span data-ttu-id="3ed00-187">**TypeCode.Empty**</span><span class="sxs-lookup"><span data-stu-id="3ed00-187">**TypeCode.Empty**</span></span>|<span data-ttu-id="3ed00-188">**VT_EMPTY**</span><span class="sxs-lookup"><span data-stu-id="3ed00-188">**VT_EMPTY**</span></span>|  
|<span data-ttu-id="3ed00-189">**TypeCode.Object**</span><span class="sxs-lookup"><span data-stu-id="3ed00-189">**TypeCode.Object**</span></span>|<span data-ttu-id="3ed00-190">**VT_UNKNOWN**</span><span class="sxs-lookup"><span data-stu-id="3ed00-190">**VT_UNKNOWN**</span></span>|  
|<span data-ttu-id="3ed00-191">**TypeCode.DBNull**</span><span class="sxs-lookup"><span data-stu-id="3ed00-191">**TypeCode.DBNull**</span></span>|<span data-ttu-id="3ed00-192">**VT_NULL**</span><span class="sxs-lookup"><span data-stu-id="3ed00-192">**VT_NULL**</span></span>|  
|<span data-ttu-id="3ed00-193">**TypeCode.Boolean**</span><span class="sxs-lookup"><span data-stu-id="3ed00-193">**TypeCode.Boolean**</span></span>|<span data-ttu-id="3ed00-194">**VT_BOOL**</span><span class="sxs-lookup"><span data-stu-id="3ed00-194">**VT_BOOL**</span></span>|  
|<span data-ttu-id="3ed00-195">**TypeCode.Char**</span><span class="sxs-lookup"><span data-stu-id="3ed00-195">**TypeCode.Char**</span></span>|<span data-ttu-id="3ed00-196">**VT_UI2**</span><span class="sxs-lookup"><span data-stu-id="3ed00-196">**VT_UI2**</span></span>|  
|<span data-ttu-id="3ed00-197">**TypeCode.Sbyte**</span><span class="sxs-lookup"><span data-stu-id="3ed00-197">**TypeCode.Sbyte**</span></span>|<span data-ttu-id="3ed00-198">**VT_I1**</span><span class="sxs-lookup"><span data-stu-id="3ed00-198">**VT_I1**</span></span>|  
|<span data-ttu-id="3ed00-199">**TypeCode.Byte**</span><span class="sxs-lookup"><span data-stu-id="3ed00-199">**TypeCode.Byte**</span></span>|<span data-ttu-id="3ed00-200">**VT_UI1**</span><span class="sxs-lookup"><span data-stu-id="3ed00-200">**VT_UI1**</span></span>|  
|<span data-ttu-id="3ed00-201">**TypeCode.Int16**</span><span class="sxs-lookup"><span data-stu-id="3ed00-201">**TypeCode.Int16**</span></span>|<span data-ttu-id="3ed00-202">**VT_I2**</span><span class="sxs-lookup"><span data-stu-id="3ed00-202">**VT_I2**</span></span>|  
|<span data-ttu-id="3ed00-203">**TypeCode.UInt16**</span><span class="sxs-lookup"><span data-stu-id="3ed00-203">**TypeCode.UInt16**</span></span>|<span data-ttu-id="3ed00-204">**VT_UI2**</span><span class="sxs-lookup"><span data-stu-id="3ed00-204">**VT_UI2**</span></span>|  
|<span data-ttu-id="3ed00-205">**TypeCode.Int32**</span><span class="sxs-lookup"><span data-stu-id="3ed00-205">**TypeCode.Int32**</span></span>|<span data-ttu-id="3ed00-206">**VT_I4**</span><span class="sxs-lookup"><span data-stu-id="3ed00-206">**VT_I4**</span></span>|  
|<span data-ttu-id="3ed00-207">**TypeCode.UInt32**</span><span class="sxs-lookup"><span data-stu-id="3ed00-207">**TypeCode.UInt32**</span></span>|<span data-ttu-id="3ed00-208">**VT_UI4**</span><span class="sxs-lookup"><span data-stu-id="3ed00-208">**VT_UI4**</span></span>|  
|<span data-ttu-id="3ed00-209">**TypeCode.Int64**</span><span class="sxs-lookup"><span data-stu-id="3ed00-209">**TypeCode.Int64**</span></span>|<span data-ttu-id="3ed00-210">**VT_I8**</span><span class="sxs-lookup"><span data-stu-id="3ed00-210">**VT_I8**</span></span>|  
|<span data-ttu-id="3ed00-211">**TypeCode.UInt64**</span><span class="sxs-lookup"><span data-stu-id="3ed00-211">**TypeCode.UInt64**</span></span>|<span data-ttu-id="3ed00-212">**VT_UI8**</span><span class="sxs-lookup"><span data-stu-id="3ed00-212">**VT_UI8**</span></span>|  
|<span data-ttu-id="3ed00-213">**TypeCode.Single**</span><span class="sxs-lookup"><span data-stu-id="3ed00-213">**TypeCode.Single**</span></span>|<span data-ttu-id="3ed00-214">**VT_R4**</span><span class="sxs-lookup"><span data-stu-id="3ed00-214">**VT_R4**</span></span>|  
|<span data-ttu-id="3ed00-215">**TypeCode.Double**</span><span class="sxs-lookup"><span data-stu-id="3ed00-215">**TypeCode.Double**</span></span>|<span data-ttu-id="3ed00-216">**VT_R8**</span><span class="sxs-lookup"><span data-stu-id="3ed00-216">**VT_R8**</span></span>|  
|<span data-ttu-id="3ed00-217">**TypeCode.Decimal**</span><span class="sxs-lookup"><span data-stu-id="3ed00-217">**TypeCode.Decimal**</span></span>|<span data-ttu-id="3ed00-218">**VT_DECIMAL**</span><span class="sxs-lookup"><span data-stu-id="3ed00-218">**VT_DECIMAL**</span></span>|  
|<span data-ttu-id="3ed00-219">**TypeCode.DateTime**</span><span class="sxs-lookup"><span data-stu-id="3ed00-219">**TypeCode.DateTime**</span></span>|<span data-ttu-id="3ed00-220">**VT_DATE**</span><span class="sxs-lookup"><span data-stu-id="3ed00-220">**VT_DATE**</span></span>|  
|<span data-ttu-id="3ed00-221">**TypeCode.String**</span><span class="sxs-lookup"><span data-stu-id="3ed00-221">**TypeCode.String**</span></span>|<span data-ttu-id="3ed00-222">**VT_BSTR**</span><span class="sxs-lookup"><span data-stu-id="3ed00-222">**VT_BSTR**</span></span>|  
|<span data-ttu-id="3ed00-223">Sem suporte.</span><span class="sxs-lookup"><span data-stu-id="3ed00-223">Not supported.</span></span>|<span data-ttu-id="3ed00-224">**VT_INT**</span><span class="sxs-lookup"><span data-stu-id="3ed00-224">**VT_INT**</span></span>|  
|<span data-ttu-id="3ed00-225">Sem suporte.</span><span class="sxs-lookup"><span data-stu-id="3ed00-225">Not supported.</span></span>|<span data-ttu-id="3ed00-226">**VT_UINT**</span><span class="sxs-lookup"><span data-stu-id="3ed00-226">**VT_UINT**</span></span>|  
|<span data-ttu-id="3ed00-227">Sem suporte.</span><span class="sxs-lookup"><span data-stu-id="3ed00-227">Not supported.</span></span>|<span data-ttu-id="3ed00-228">**VT_ARRAY**</span><span class="sxs-lookup"><span data-stu-id="3ed00-228">**VT_ARRAY**</span></span>|  
|<span data-ttu-id="3ed00-229">Sem suporte.</span><span class="sxs-lookup"><span data-stu-id="3ed00-229">Not supported.</span></span>|<span data-ttu-id="3ed00-230">**VT_RECORD**</span><span class="sxs-lookup"><span data-stu-id="3ed00-230">**VT_RECORD**</span></span>|  
|<span data-ttu-id="3ed00-231">Sem suporte.</span><span class="sxs-lookup"><span data-stu-id="3ed00-231">Not supported.</span></span>|<span data-ttu-id="3ed00-232">**VT_CY**</span><span class="sxs-lookup"><span data-stu-id="3ed00-232">**VT_CY**</span></span>|  
|<span data-ttu-id="3ed00-233">Sem suporte.</span><span class="sxs-lookup"><span data-stu-id="3ed00-233">Not supported.</span></span>|<span data-ttu-id="3ed00-234">**VT_VARIANT**</span><span class="sxs-lookup"><span data-stu-id="3ed00-234">**VT_VARIANT**</span></span>|  
  
 <span data-ttu-id="3ed00-235">O valor da variante COM é determinado com uma chamada à interface **IConvertible.To** *Type*, em que **To** *Type* é a rotina de conversão que corresponde ao tipo retornado do **IConvertible.GetTypeCode**.</span><span class="sxs-lookup"><span data-stu-id="3ed00-235">The value of the COM variant is determined by calling the **IConvertible.To** *Type* interface, where **To** *Type* is the conversion routine that corresponds to the type that was returned from **IConvertible.GetTypeCode**.</span></span> <span data-ttu-id="3ed00-236">Por exemplo, um objeto que retorna **TypeCode.Double** de **IConvertible.GetTypeCode** tem o marshaling realizado como uma variante COM do tipo **VT_R8**.</span><span class="sxs-lookup"><span data-stu-id="3ed00-236">For example, an object that returns **TypeCode.Double** from **IConvertible.GetTypeCode** is marshaled as a COM variant of type **VT_R8**.</span></span> <span data-ttu-id="3ed00-237">É possível obter o valor da variante (armazenado no campo **dblVal** da variante COM) com a conversão para a interface **IConvertible** e uma chamada ao método <xref:System.IConvertible.ToDouble%2A>.</span><span class="sxs-lookup"><span data-stu-id="3ed00-237">You can obtain the value of the variant (stored in the **dblVal** field of the COM variant) by casting to the **IConvertible** interface and calling the <xref:System.IConvertible.ToDouble%2A> method.</span></span>  
  
<a name="cpcondefaultmarshalingforobjectsanchor4"></a>   
## <a name="marshaling-variant-to-object"></a><span data-ttu-id="3ed00-238">Realizando marshaling de variante para objeto</span><span class="sxs-lookup"><span data-stu-id="3ed00-238">Marshaling Variant to Object</span></span>  
 <span data-ttu-id="3ed00-239">Ao realizar marshaling de uma variante para um objeto, o tipo e, às vezes, o valor, da variante com marshaling determina o tipo de objeto produzido.</span><span class="sxs-lookup"><span data-stu-id="3ed00-239">When marshaling a variant to an object, the type, and sometimes the value, of the marshaled variant determines the type of object produced.</span></span> <span data-ttu-id="3ed00-240">A tabela a seguir identifica cada tipo de variante e o tipo de objeto correspondente criado pelo marshaler quando uma variante é passada do COM para o .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="3ed00-240">The following table identifies each variant type and the corresponding object type that the marshaler creates when a variant is passed from COM to the .NET Framework.</span></span>  
  
|<span data-ttu-id="3ed00-241">Tipo de variante COM</span><span class="sxs-lookup"><span data-stu-id="3ed00-241">COM variant type</span></span>|<span data-ttu-id="3ed00-242">Tipo de objeto</span><span class="sxs-lookup"><span data-stu-id="3ed00-242">Object type</span></span>|  
|----------------------|-----------------|  
|<span data-ttu-id="3ed00-243">**VT_EMPTY**</span><span class="sxs-lookup"><span data-stu-id="3ed00-243">**VT_EMPTY**</span></span>|<span data-ttu-id="3ed00-244">Referência de objeto nulo (**Nothing** no Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="3ed00-244">Null object reference (**Nothing** in Visual Basic).</span></span>|  
|<span data-ttu-id="3ed00-245">**VT_NULL**</span><span class="sxs-lookup"><span data-stu-id="3ed00-245">**VT_NULL**</span></span>|<xref:System.DBNull?displayProperty=nameWithType>|  
|<span data-ttu-id="3ed00-246">**VT_DISPATCH**</span><span class="sxs-lookup"><span data-stu-id="3ed00-246">**VT_DISPATCH**</span></span>|<span data-ttu-id="3ed00-247">**System.__ComObject** ou nulo se (pdispVal == null)</span><span class="sxs-lookup"><span data-stu-id="3ed00-247">**System.__ComObject** or null if (pdispVal == null)</span></span>|  
|<span data-ttu-id="3ed00-248">**VT_UNKNOWN**</span><span class="sxs-lookup"><span data-stu-id="3ed00-248">**VT_UNKNOWN**</span></span>|<span data-ttu-id="3ed00-249">**System.__ComObject** ou nulo se (punkVal == null)</span><span class="sxs-lookup"><span data-stu-id="3ed00-249">**System.__ComObject** or null if (punkVal == null)</span></span>|  
|<span data-ttu-id="3ed00-250">**VT_ERROR**</span><span class="sxs-lookup"><span data-stu-id="3ed00-250">**VT_ERROR**</span></span>|<xref:System.UInt32?displayProperty=nameWithType>|  
|<span data-ttu-id="3ed00-251">**VT_BOOL**</span><span class="sxs-lookup"><span data-stu-id="3ed00-251">**VT_BOOL**</span></span>|<xref:System.Boolean?displayProperty=nameWithType>|  
|<span data-ttu-id="3ed00-252">**VT_I1**</span><span class="sxs-lookup"><span data-stu-id="3ed00-252">**VT_I1**</span></span>|<xref:System.SByte?displayProperty=nameWithType>|  
|<span data-ttu-id="3ed00-253">**VT_UI1**</span><span class="sxs-lookup"><span data-stu-id="3ed00-253">**VT_UI1**</span></span>|<xref:System.Byte?displayProperty=nameWithType>|  
|<span data-ttu-id="3ed00-254">**VT_I2**</span><span class="sxs-lookup"><span data-stu-id="3ed00-254">**VT_I2**</span></span>|<xref:System.Int16?displayProperty=nameWithType>|  
|<span data-ttu-id="3ed00-255">**VT_UI2**</span><span class="sxs-lookup"><span data-stu-id="3ed00-255">**VT_UI2**</span></span>|<xref:System.UInt16?displayProperty=nameWithType>|  
|<span data-ttu-id="3ed00-256">**VT_I4**</span><span class="sxs-lookup"><span data-stu-id="3ed00-256">**VT_I4**</span></span>|<xref:System.Int32?displayProperty=nameWithType>|  
|<span data-ttu-id="3ed00-257">**VT_UI4**</span><span class="sxs-lookup"><span data-stu-id="3ed00-257">**VT_UI4**</span></span>|<xref:System.UInt32?displayProperty=nameWithType>|  
|<span data-ttu-id="3ed00-258">**VT_I8**</span><span class="sxs-lookup"><span data-stu-id="3ed00-258">**VT_I8**</span></span>|<xref:System.Int64?displayProperty=nameWithType>|  
|<span data-ttu-id="3ed00-259">**VT_UI8**</span><span class="sxs-lookup"><span data-stu-id="3ed00-259">**VT_UI8**</span></span>|<xref:System.UInt64?displayProperty=nameWithType>|  
|<span data-ttu-id="3ed00-260">**VT_R4**</span><span class="sxs-lookup"><span data-stu-id="3ed00-260">**VT_R4**</span></span>|<xref:System.Single?displayProperty=nameWithType>|  
|<span data-ttu-id="3ed00-261">**VT_R8**</span><span class="sxs-lookup"><span data-stu-id="3ed00-261">**VT_R8**</span></span>|<xref:System.Double?displayProperty=nameWithType>|  
|<span data-ttu-id="3ed00-262">**VT_DECIMAL**</span><span class="sxs-lookup"><span data-stu-id="3ed00-262">**VT_DECIMAL**</span></span>|<xref:System.Decimal?displayProperty=nameWithType>|  
|<span data-ttu-id="3ed00-263">**VT_DATE**</span><span class="sxs-lookup"><span data-stu-id="3ed00-263">**VT_DATE**</span></span>|<xref:System.DateTime?displayProperty=nameWithType>|  
|<span data-ttu-id="3ed00-264">**VT_BSTR**</span><span class="sxs-lookup"><span data-stu-id="3ed00-264">**VT_BSTR**</span></span>|<xref:System.String?displayProperty=nameWithType>|  
|<span data-ttu-id="3ed00-265">**VT_INT**</span><span class="sxs-lookup"><span data-stu-id="3ed00-265">**VT_INT**</span></span>|<xref:System.Int32?displayProperty=nameWithType>|  
|<span data-ttu-id="3ed00-266">**VT_UINT**</span><span class="sxs-lookup"><span data-stu-id="3ed00-266">**VT_UINT**</span></span>|<xref:System.UInt32?displayProperty=nameWithType>|  
|<span data-ttu-id="3ed00-267">**VT_ARRAY** &#124; **VT_\***</span><span class="sxs-lookup"><span data-stu-id="3ed00-267">**VT_ARRAY** &#124; **VT_\***</span></span>|<xref:System.Array?displayProperty=nameWithType>|  
|<span data-ttu-id="3ed00-268">**VT_CY**</span><span class="sxs-lookup"><span data-stu-id="3ed00-268">**VT_CY**</span></span>|<xref:System.Decimal?displayProperty=nameWithType>|  
|<span data-ttu-id="3ed00-269">**VT_RECORD**</span><span class="sxs-lookup"><span data-stu-id="3ed00-269">**VT_RECORD**</span></span>|<span data-ttu-id="3ed00-270">Tipo de valor demarcado correspondente.</span><span class="sxs-lookup"><span data-stu-id="3ed00-270">Corresponding boxed value type.</span></span>|  
|<span data-ttu-id="3ed00-271">**VT_VARIANT**</span><span class="sxs-lookup"><span data-stu-id="3ed00-271">**VT_VARIANT**</span></span>|<span data-ttu-id="3ed00-272">Sem suporte.</span><span class="sxs-lookup"><span data-stu-id="3ed00-272">Not supported.</span></span>|  
  
 <span data-ttu-id="3ed00-273">Os tipos de variante passados do COM para o código gerenciado e, em seguida, novamente para o COM podem não manter o mesmo tipo de variante durante a chamada.</span><span class="sxs-lookup"><span data-stu-id="3ed00-273">Variant types passed from COM to managed code and then back to COM might not retain the same variant type for the duration of the call.</span></span> <span data-ttu-id="3ed00-274">Considere o que acontece quando uma variante do tipo **VT_DISPATCH** é passada do COM para o .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="3ed00-274">Consider what happens when a variant of type **VT_DISPATCH** is passed from COM to the .NET Framework.</span></span> <span data-ttu-id="3ed00-275">Durante o marshaling, a variante é convertida em um <xref:System.Object?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="3ed00-275">During marshaling, the variant is converted to a <xref:System.Object?displayProperty=nameWithType>.</span></span> <span data-ttu-id="3ed00-276">Se o **Object** for então passado novamente para o COM, ele terá o marshaling realizado novamente como uma variante do tipo **VT_UNKNOWN**.</span><span class="sxs-lookup"><span data-stu-id="3ed00-276">If the **Object** is then passed back to COM, it is marshaled back to a variant of type **VT_UNKNOWN**.</span></span> <span data-ttu-id="3ed00-277">Não há nenhuma garantia de que a variante produzida quando um objeto tem o marshaling realizado de um código gerenciado para o COM terá o mesmo tipo de variante usado inicialmente para produzir o objeto.</span><span class="sxs-lookup"><span data-stu-id="3ed00-277">There is no guarantee that the variant produced when an object is marshaled from managed code to COM will be the same type as the variant initially used to produce the object.</span></span>  
  
<a name="cpcondefaultmarshalingforobjectsanchor6"></a>   
## <a name="marshaling-byref-variants"></a><span data-ttu-id="3ed00-278">Realizando marshaling de variantes de ByRef</span><span class="sxs-lookup"><span data-stu-id="3ed00-278">Marshaling ByRef Variants</span></span>  
 <span data-ttu-id="3ed00-279">Embora as próprias variantes possam ser passadas por valor ou por referência, o sinalizador **VT_BYREF** também pode ser usado com qualquer tipo de variante para indicar que o conteúdo da variante está sendo passado por referência, em vez de por valor.</span><span class="sxs-lookup"><span data-stu-id="3ed00-279">Although variants themselves can be passed by value or by reference, the **VT_BYREF** flag can also be used with any variant type to indicate that the contents of the variant are being passed by reference instead of by value.</span></span> <span data-ttu-id="3ed00-280">A diferença entre realizar marshaling de variantes por referência e realizar marshaling de uma variante com o sinalizador **VT_BYREF** definido pode ser confusa.</span><span class="sxs-lookup"><span data-stu-id="3ed00-280">The difference between marshaling variants by reference and marshaling a variant with the **VT_BYREF** flag set can be confusing.</span></span> <span data-ttu-id="3ed00-281">A ilustração a seguir esclarece as diferenças.</span><span class="sxs-lookup"><span data-stu-id="3ed00-281">The following illustration clarifies the differences.</span></span>  
  
 <span data-ttu-id="3ed00-282">![Variante passada na pilha](./media/interopvariant.gif "interopvariant")</span><span class="sxs-lookup"><span data-stu-id="3ed00-282">![Variant passed on the stack](./media/interopvariant.gif "interopvariant")</span></span>  
<span data-ttu-id="3ed00-283">Variantes passadas por valor e por referência</span><span class="sxs-lookup"><span data-stu-id="3ed00-283">Variants passed by value and by reference</span></span>  
  
 <span data-ttu-id="3ed00-284">**Comportamento padrão de marshaling de objetos e variantes por valor**</span><span class="sxs-lookup"><span data-stu-id="3ed00-284">**Default behavior for marshaling objects and variants by value**</span></span>  
  
-   <span data-ttu-id="3ed00-285">Ao passar objetos do código gerenciado para o COM, o conteúdo do objeto é copiado para uma nova variante criada pelo marshaler, usando as regras definidas em [Realizando marshaling de objeto para variante](#cpcondefaultmarshalingforobjectsanchor3).</span><span class="sxs-lookup"><span data-stu-id="3ed00-285">When passing objects from managed code to COM, the contents of the object are copied into a new variant created by the marshaler, using the rules defined in [Marshaling Object to Variant](#cpcondefaultmarshalingforobjectsanchor3).</span></span> <span data-ttu-id="3ed00-286">As alterações feitas na variante no lado não gerenciado não são propagadas novamente para o objeto original após o retorno da chamada.</span><span class="sxs-lookup"><span data-stu-id="3ed00-286">Changes made to the variant on the unmanaged side are not propagated back to the original object on return from the call.</span></span>  
  
-   <span data-ttu-id="3ed00-287">Ao passar variantes do COM para o código gerenciado, o conteúdo da variante é copiado para um objeto recém-criado, usando as regras definidas em [Realizando marshaling de variante para objeto](#cpcondefaultmarshalingforobjectsanchor4).</span><span class="sxs-lookup"><span data-stu-id="3ed00-287">When passing variants from COM to managed code, the contents of the variant are copied to a newly created object, using the rules defined in [Marshaling Variant to Object](#cpcondefaultmarshalingforobjectsanchor4).</span></span> <span data-ttu-id="3ed00-288">As alterações feitas no objeto no lado gerenciado não são propagadas novamente para a variante original após o retorno da chamada.</span><span class="sxs-lookup"><span data-stu-id="3ed00-288">Changes made to the object on the managed side are not propagated back to the original variant on return from the call.</span></span>  
  
 <span data-ttu-id="3ed00-289">**Comportamento padrão de marshaling de objetos e variantes por referência**</span><span class="sxs-lookup"><span data-stu-id="3ed00-289">**Default behavior for marshaling objects and variants by reference**</span></span>  
  
 <span data-ttu-id="3ed00-290">Para propagar as alterações novamente para o chamador, os parâmetros devem ser passados por referência.</span><span class="sxs-lookup"><span data-stu-id="3ed00-290">To propagate changes back to the caller, the parameters must be passed by reference.</span></span> <span data-ttu-id="3ed00-291">Por exemplo, use a palavra-chave **ref** no C# (ou **ByRef** no código gerenciado do Visual Basic) para passar parâmetros por referência.</span><span class="sxs-lookup"><span data-stu-id="3ed00-291">For example, you can use the **ref** keyword in C# (or **ByRef** in Visual Basic managed code) to pass parameters by reference.</span></span> <span data-ttu-id="3ed00-292">No COM, os parâmetros de referência são passados usando um ponteiro, como uma **variante \***.</span><span class="sxs-lookup"><span data-stu-id="3ed00-292">In COM, reference parameters are passed using a pointer such as a **variant \***.</span></span>  
  
-   <span data-ttu-id="3ed00-293">Ao passar um objeto para o COM por referência, o marshaler cria uma nova variante e copia o conteúdo da referência de objeto para a variante antes que a chamada seja feita.</span><span class="sxs-lookup"><span data-stu-id="3ed00-293">When passing an object to COM by reference, the marshaler creates a new variant and copies the contents of the object reference into the variant before the call is made.</span></span> <span data-ttu-id="3ed00-294">A variante é passada para a função não gerenciada, na qual o usuário é livre para alterar o conteúdo da variante.</span><span class="sxs-lookup"><span data-stu-id="3ed00-294">The variant is passed to the unmanaged function where the user is free to change the contents of the variant.</span></span> <span data-ttu-id="3ed00-295">Após o retorno da chamada, todas as alterações feitas na variante no lado não gerenciado são propagadas novamente para o objeto original.</span><span class="sxs-lookup"><span data-stu-id="3ed00-295">On return from the call, any changes made to the variant on the unmanaged side are propagated back to the original object.</span></span> <span data-ttu-id="3ed00-296">Se o tipo da variante for diferente do tipo da variante passada para a chamada, as alterações serão propagadas novamente para um objeto de um tipo diferente.</span><span class="sxs-lookup"><span data-stu-id="3ed00-296">If the type of the variant differs from the type of the variant passed to the call, then the changes are propagated back to an object of a different type.</span></span> <span data-ttu-id="3ed00-297">Ou seja, o tipo do objeto passado para a chamada pode ser diferente do tipo do objeto retornado da chamada.</span><span class="sxs-lookup"><span data-stu-id="3ed00-297">That is, the type of the object passed into the call can differ from the type of the object returned from the call.</span></span>  
  
-   <span data-ttu-id="3ed00-298">Ao passar uma variante para um código gerenciado por referência, o marshaler cria um novo objeto e copia o conteúdo da variante para o objeto antes de fazer a chamada.</span><span class="sxs-lookup"><span data-stu-id="3ed00-298">When passing a variant to managed code by reference, the marshaler creates a new object and copies the contents of the variant into the object before making the call.</span></span> <span data-ttu-id="3ed00-299">Uma referência ao objeto é passada para a função gerenciada, em que o usuário é livre para alterar o objeto.</span><span class="sxs-lookup"><span data-stu-id="3ed00-299">A reference to the object is passed to the managed function, where the user is free to change the object.</span></span> <span data-ttu-id="3ed00-300">Após o retorno da chamada, todas as alterações feitas no objeto referenciado são propagadas novamente para a variante original.</span><span class="sxs-lookup"><span data-stu-id="3ed00-300">On return from the call, any changes made to the referenced object are propagated back to the original variant.</span></span> <span data-ttu-id="3ed00-301">Se o tipo do objeto for diferente do tipo do objeto passado para a chamada, o tipo da variante original será alterado e o valor será propagado novamente para a variante.</span><span class="sxs-lookup"><span data-stu-id="3ed00-301">If the type of the object differs from the type of the object passed in to the call, the type of the original variant is changed and the value is propagated back into the variant.</span></span> <span data-ttu-id="3ed00-302">Novamente, o tipo da variante passado para a chamada pode ser diferente do tipo da variante retornado da chamada.</span><span class="sxs-lookup"><span data-stu-id="3ed00-302">Again, the type of the variant passed into the call can differ from the type of the variant returned from the call.</span></span>  
  
 <span data-ttu-id="3ed00-303">**Comportamento padrão de marshaling de uma variante com o sinalizador VT_BYREF definido**</span><span class="sxs-lookup"><span data-stu-id="3ed00-303">**Default behavior for marshaling a variant with the VT_BYREF flag set**</span></span>  
  
-   <span data-ttu-id="3ed00-304">Uma variante que está sendo passada para o código gerenciado por valor pode ter o sinalizador **VT_BYREF** definido para indicar que a variante contém uma referência, em vez de um valor.</span><span class="sxs-lookup"><span data-stu-id="3ed00-304">A variant being passed to managed code by value can have the **VT_BYREF** flag set to indicate that the variant contains a reference instead of a value.</span></span> <span data-ttu-id="3ed00-305">Nesse caso, a variante ainda tem o marshaling realizado para um objeto porque a variante está sendo passada por valor.</span><span class="sxs-lookup"><span data-stu-id="3ed00-305">In this case, the variant is still marshaled to an object because the variant is being passed by value.</span></span> <span data-ttu-id="3ed00-306">O marshaler desreferencia automaticamente o conteúdo da variante e o copia para um objeto recém-criado antes de fazer a chamada.</span><span class="sxs-lookup"><span data-stu-id="3ed00-306">The marshaler automatically dereferences the contents of the variant and copies it into a newly created object before making the call.</span></span> <span data-ttu-id="3ed00-307">Em seguida, o objeto é passado para a função gerenciada; no entanto, após o retorno da chamada, o objeto não é propagado novamente para a variante original.</span><span class="sxs-lookup"><span data-stu-id="3ed00-307">The object is then passed into the managed function; however, on return from the call, the object is not propagated back into the original variant.</span></span> <span data-ttu-id="3ed00-308">As alterações feitas no objeto gerenciado são perdidas.</span><span class="sxs-lookup"><span data-stu-id="3ed00-308">Changes made to the managed object are lost.</span></span>  
  
    > [!CAUTION]
    >  <span data-ttu-id="3ed00-309">Não há nenhuma maneira de alterar o valor de uma variante passada por valor, mesmo se a variante tiver um sinalizador **VT_BYREF** definido.</span><span class="sxs-lookup"><span data-stu-id="3ed00-309">There is no way to change the value of a variant passed by value, even if the variant has the **VT_BYREF** flag set.</span></span>  
  
-   <span data-ttu-id="3ed00-310">Uma variante que está sendo passada para o código gerenciado por referência também pode ter o sinalizador **VT_BYREF** definido para indicar que a variante contém outra referência.</span><span class="sxs-lookup"><span data-stu-id="3ed00-310">A variant being passed to managed code by reference can also have the **VT_BYREF** flag set to indicate that the variant contains another reference.</span></span> <span data-ttu-id="3ed00-311">Nesse caso, a variante tem o marshaling realizado para um objeto **ref** porque a variante está sendo passada por referência.</span><span class="sxs-lookup"><span data-stu-id="3ed00-311">If it does, the variant is marshaled to a **ref** object because the variant is being passed by reference.</span></span> <span data-ttu-id="3ed00-312">O marshaler desreferencia automaticamente o conteúdo da variante e o copia para um objeto recém-criado antes de fazer a chamada.</span><span class="sxs-lookup"><span data-stu-id="3ed00-312">The marshaler automatically dereferences the contents of the variant and copies it into a newly created object before making the call.</span></span> <span data-ttu-id="3ed00-313">Após o retorno da chamada, o valor do objeto é propagado novamente para a referência dentro da variante original somente se o objeto é do mesmo tipo do objeto passado.</span><span class="sxs-lookup"><span data-stu-id="3ed00-313">On return from the call, the value of the object is propagated back to the reference within the original variant only if the object is the same type as the object passed in.</span></span> <span data-ttu-id="3ed00-314">Ou seja, a propagação não altera o tipo de uma variante com o sinalizador **VT_BYREF** definido.</span><span class="sxs-lookup"><span data-stu-id="3ed00-314">That is, propagation does not change the type of a variant with the **VT_BYREF** flag set.</span></span> <span data-ttu-id="3ed00-315">Se o tipo do objeto for alterado durante a chamada, ocorrerá uma <xref:System.InvalidCastException> após o retorno da chamada.</span><span class="sxs-lookup"><span data-stu-id="3ed00-315">If the type of the object is changed during the call, an <xref:System.InvalidCastException> occurs on return from the call.</span></span>  
  
 <span data-ttu-id="3ed00-316">A tabela a seguir resume as regras de propagação para variantes e objetos.</span><span class="sxs-lookup"><span data-stu-id="3ed00-316">The following table summarizes the propagation rules for variants and objects.</span></span>  
  
|<span data-ttu-id="3ed00-317">De</span><span class="sxs-lookup"><span data-stu-id="3ed00-317">From</span></span>|<span data-ttu-id="3ed00-318">Para</span><span class="sxs-lookup"><span data-stu-id="3ed00-318">To</span></span>|<span data-ttu-id="3ed00-319">Alterações propagadas novamente</span><span class="sxs-lookup"><span data-stu-id="3ed00-319">Changes propagated back</span></span>|  
|----------|--------|-----------------------------|  
|<span data-ttu-id="3ed00-320">**Variante**  *v*</span><span class="sxs-lookup"><span data-stu-id="3ed00-320">**Variant**  *v*</span></span>|<span data-ttu-id="3ed00-321">**Objeto**  *o*</span><span class="sxs-lookup"><span data-stu-id="3ed00-321">**Object**  *o*</span></span>|<span data-ttu-id="3ed00-322">Nunca</span><span class="sxs-lookup"><span data-stu-id="3ed00-322">Never</span></span>|  
|<span data-ttu-id="3ed00-323">**Objeto**  *o*</span><span class="sxs-lookup"><span data-stu-id="3ed00-323">**Object**  *o*</span></span>|<span data-ttu-id="3ed00-324">**Variante**  *v*</span><span class="sxs-lookup"><span data-stu-id="3ed00-324">**Variant**  *v*</span></span>|<span data-ttu-id="3ed00-325">Nunca</span><span class="sxs-lookup"><span data-stu-id="3ed00-325">Never</span></span>|  
|<span data-ttu-id="3ed00-326">**Variante**   ***\****  *pv*</span><span class="sxs-lookup"><span data-stu-id="3ed00-326">**Variant**   ***\****  *pv*</span></span>|<span data-ttu-id="3ed00-327">**Objeto de Referência**  *o*</span><span class="sxs-lookup"><span data-stu-id="3ed00-327">**Ref Object**  *o*</span></span>|<span data-ttu-id="3ed00-328">Sempre</span><span class="sxs-lookup"><span data-stu-id="3ed00-328">Always</span></span>|  
|<span data-ttu-id="3ed00-329">**Objeto de referência**  *o*</span><span class="sxs-lookup"><span data-stu-id="3ed00-329">**Ref object**  *o*</span></span>|<span data-ttu-id="3ed00-330">**Variante**   ***\****  *pv*</span><span class="sxs-lookup"><span data-stu-id="3ed00-330">**Variant**   ***\****  *pv*</span></span>|<span data-ttu-id="3ed00-331">Sempre</span><span class="sxs-lookup"><span data-stu-id="3ed00-331">Always</span></span>|  
|<span data-ttu-id="3ed00-332">**Variante**  *v* **(VT_BYREF** *&#124;* **VT_\*)**</span><span class="sxs-lookup"><span data-stu-id="3ed00-332">**Variant**  *v* **(VT_BYREF** *&#124;* **VT_\*)**</span></span>|<span data-ttu-id="3ed00-333">**Objeto**  *o*</span><span class="sxs-lookup"><span data-stu-id="3ed00-333">**Object**  *o*</span></span>|<span data-ttu-id="3ed00-334">Nunca</span><span class="sxs-lookup"><span data-stu-id="3ed00-334">Never</span></span>|  
|<span data-ttu-id="3ed00-335">**Variante**  *v* **(VT_BYREF** *&#124;* **VT_)**</span><span class="sxs-lookup"><span data-stu-id="3ed00-335">**Variant**  *v* **(VT_BYREF** *&#124;* **VT_)**</span></span>|<span data-ttu-id="3ed00-336">**Objeto de Referência**  *o*</span><span class="sxs-lookup"><span data-stu-id="3ed00-336">**Ref Object**  *o*</span></span>|<span data-ttu-id="3ed00-337">Somente se o tipo não foi alterado.</span><span class="sxs-lookup"><span data-stu-id="3ed00-337">Only if the type has not changed.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="3ed00-338">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3ed00-338">See Also</span></span>  
 [<span data-ttu-id="3ed00-339">Comportamento de marshaling padrão</span><span class="sxs-lookup"><span data-stu-id="3ed00-339">Default Marshaling Behavior</span></span>](default-marshaling-behavior.md)  
 [<span data-ttu-id="3ed00-340">Tipos blittable e não blittable</span><span class="sxs-lookup"><span data-stu-id="3ed00-340">Blittable and Non-Blittable Types</span></span>](blittable-and-non-blittable-types.md)  
 <span data-ttu-id="3ed00-341">[Atributos direcionais](https://msdn.microsoft.com/library/241ac5b5-928e-4969-8f58-1dbc048f9ea2(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="3ed00-341">[Directional Attributes](https://msdn.microsoft.com/library/241ac5b5-928e-4969-8f58-1dbc048f9ea2(v=vs.100))</span></span>  
 [<span data-ttu-id="3ed00-342">Copiando e fixando</span><span class="sxs-lookup"><span data-stu-id="3ed00-342">Copying and Pinning</span></span>](copying-and-pinning.md)
