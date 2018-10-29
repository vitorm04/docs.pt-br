---
title: Visão geral do modelo de programação atribuído (MEF)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- MEF, attributed programming model
- attributed programming model [MEF]
ms.assetid: 49b787ff-2741-4836-ad51-c3017dc592d4
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7dab1474454f8169d8d0d80413c6fb95677fb4bf
ms.sourcegitcommit: b22705f1540b237c566721018f974822d5cd8758
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/19/2018
ms.locfileid: "49453380"
---
# <a name="attributed-programming-model-overview-mef"></a><span data-ttu-id="aea3b-102">Visão geral do modelo de programação atribuído (MEF)</span><span class="sxs-lookup"><span data-stu-id="aea3b-102">Attributed Programming Model Overview (MEF)</span></span>
<span data-ttu-id="aea3b-103">No MEF (Managed Extensibility Framework), um *modelo de programação* é um método específico para definir o conjunto de objetos conceituais no qual o MEF opera.</span><span class="sxs-lookup"><span data-stu-id="aea3b-103">In the Managed Extensibility Framework (MEF), a *programming model* is a particular method of defining the set of conceptual objects on which MEF operates.</span></span> <span data-ttu-id="aea3b-104">Esses objetos conceituais incluem partes, importações e exportações.</span><span class="sxs-lookup"><span data-stu-id="aea3b-104">These conceptual objects include parts, imports, and exports.</span></span> <span data-ttu-id="aea3b-105">O MEF usa esses objetos, mas não especifica como eles devem ser representados.</span><span class="sxs-lookup"><span data-stu-id="aea3b-105">MEF uses these objects, but does not specify how they should be represented.</span></span> <span data-ttu-id="aea3b-106">Portanto, uma grande variedade de modelos de programação são possíveis, incluindo modelos de programação personalizados.</span><span class="sxs-lookup"><span data-stu-id="aea3b-106">Therefore, a wide variety of programming models are possible, including customized programming models.</span></span>  
  
 <span data-ttu-id="aea3b-107">O modelo de programação padrão usado no MEF é o *modelo de programação atribuído*.</span><span class="sxs-lookup"><span data-stu-id="aea3b-107">The default programming model used in MEF is the *attributed programming model*.</span></span> <span data-ttu-id="aea3b-108">No modelo de programação atribuída, partes, importações, exportações e outros objetos são definidos com atributos que decoram classes comuns do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="aea3b-108">In the attributed programming model parts, imports, exports, and other objects are defined with attributes that decorate ordinary .NET Framework classes.</span></span> <span data-ttu-id="aea3b-109">Este tópico explica como usar os atributos fornecidos pelo modelo de programação atribuída para criar um aplicativo MEF.</span><span class="sxs-lookup"><span data-stu-id="aea3b-109">This topic explains how to use the attributes provided by the attributed programming model to create a MEF application.</span></span>  
  
<a name="import_and_export_basics"></a>   
## <a name="import-and-export-basics"></a><span data-ttu-id="aea3b-110">Fundamentos sobre importações e exportações</span><span class="sxs-lookup"><span data-stu-id="aea3b-110">Import and Export Basics</span></span>  
 <span data-ttu-id="aea3b-111">Uma *exportação* é um valor que uma parte fornece a outras partes no contêiner, e uma *importação* é um requisito que uma parte expressa ao contêiner, a ser preenchido com as exportações disponíveis.</span><span class="sxs-lookup"><span data-stu-id="aea3b-111">An *export* is a value that a part provides to other parts in the container, and an *import* is a requirement that a part expresses to the container, to be filled from the available exports.</span></span> <span data-ttu-id="aea3b-112">No modelo de programação atribuída, importações e exportações são declaradas decorando classes ou membros com os atributos `Import` e `Export`.</span><span class="sxs-lookup"><span data-stu-id="aea3b-112">In the attributed programming model, imports and exports are declared by decorating classes or members with the `Import` and `Export` attributes.</span></span> <span data-ttu-id="aea3b-113">O atributo `Export` pode decorar uma classe, um campo, propriedade ou método, enquanto o atributo `Import` pode decorar um parâmetro de campo, propriedade ou construtor.</span><span class="sxs-lookup"><span data-stu-id="aea3b-113">The `Export` attribute can decorate a class, field, property, or method, while the `Import` attribute can decorate a field, property, or constructor parameter.</span></span>  
  
 <span data-ttu-id="aea3b-114">Para que uma importação seja correspondida a uma exportação, a importação e a exportação devem ter o mesmo *contrato*.</span><span class="sxs-lookup"><span data-stu-id="aea3b-114">In order for an import to be matched with an export, the import and export must have the same *contract*.</span></span> <span data-ttu-id="aea3b-115">O contrato é formado por uma cadeia de caracteres, chamada *nome do contrato*, e pelo tipo de objeto exportado ou importado, chamado de *tipo de contrato*.</span><span class="sxs-lookup"><span data-stu-id="aea3b-115">The contract consists of a string, called the *contract name*, and the type of the exported or imported object, called the *contract type*.</span></span> <span data-ttu-id="aea3b-116">Somente se o nome do contrato e o tipo de contrato corresponderem, uma exportação é considerada para atender uma importação específica.</span><span class="sxs-lookup"><span data-stu-id="aea3b-116">Only if both the contract name and contract type match is an export considered to fulfill a particular import.</span></span>  
  
 <span data-ttu-id="aea3b-117">Um ou os dois parâmetros do contrato podem ser implícitos ou explícitos.</span><span class="sxs-lookup"><span data-stu-id="aea3b-117">Either or both of the contract parameters can be implicit or explicit.</span></span> <span data-ttu-id="aea3b-118">O código a seguir mostra uma classe que declara uma importação básica.</span><span class="sxs-lookup"><span data-stu-id="aea3b-118">The following code shows a class that declares a basic import.</span></span>  
  
```vb  
Public Class MyClass1  
    <Import()>  
    Public Property MyAddin As IMyAddin  
End Class  
```  
  
```csharp  
public class MyClass  
{  
    [Import]  
    public IMyAddin MyAddin { get; set; }  
}  
```  
  
 <span data-ttu-id="aea3b-119">Nessa importação, o atributo `Import` não tem um parâmetro de tipo de contrato, nem de nome de contrato anexado.</span><span class="sxs-lookup"><span data-stu-id="aea3b-119">In this import, the `Import` attribute has neither a contract type nor a contract name parameter attached.</span></span> <span data-ttu-id="aea3b-120">Portanto, ambos serão inferidos da propriedade decorada.</span><span class="sxs-lookup"><span data-stu-id="aea3b-120">Therefore, both will be inferred from the decorated property.</span></span> <span data-ttu-id="aea3b-121">Nesse caso, o tipo de contrato será `IMyAddin`, e o nome do contrato será uma cadeia de caracteres exclusiva criada do tipo de contrato.</span><span class="sxs-lookup"><span data-stu-id="aea3b-121">In this case, the contract type will be `IMyAddin`, and the contract name will be a unique string created from the contract type.</span></span> <span data-ttu-id="aea3b-122">(Em outras palavras, o nome do contrato corresponderá somente às exportações cujos nomes também sejam inferidos do tipo `IMyAddin`.)</span><span class="sxs-lookup"><span data-stu-id="aea3b-122">(In other words, the contract name will match only exports whose names are also inferred from the type `IMyAddin`.)</span></span>  
  
 <span data-ttu-id="aea3b-123">Segue uma exportação que corresponde à importação anterior.</span><span class="sxs-lookup"><span data-stu-id="aea3b-123">The following shows an export that matches the previous import.</span></span>  
  
```vb  
<Export(GetType(IMyAddin))>  
Public Class MyLogger  
    Implements IMyAddin  
  
End Class  
```  
  
```csharp  
[Export(typeof(IMyAddin))]  
public class MyLogger : IMyAddin { }  
```  
  
 <span data-ttu-id="aea3b-124">Nessa exportação, o tipo de contrato é `IMyAddin`, pois ele é especificado como parâmetro do atributo `Export`.</span><span class="sxs-lookup"><span data-stu-id="aea3b-124">In this export, the contract type is `IMyAddin` because it is specified as a parameter of the `Export` attribute.</span></span> <span data-ttu-id="aea3b-125">O tipo exportado deve ser igual ao tipo de contrato, ser derivado do tipo de contrato ou implementar o tipo de contrato, caso seja uma instância.</span><span class="sxs-lookup"><span data-stu-id="aea3b-125">The exported type must be either the same as the contract type, derive from the contract type, or implement the contract type if it is an interface.</span></span> <span data-ttu-id="aea3b-126">Nessa exportação, o tipo real `MyLogger` implementa a interface `IMyAddin`.</span><span class="sxs-lookup"><span data-stu-id="aea3b-126">In this export, the actual type `MyLogger` implements the interface `IMyAddin`.</span></span> <span data-ttu-id="aea3b-127">O nome do contrato é inferido do tipo de contrato, o que significa que essa exportação corresponderá à importação anterior.</span><span class="sxs-lookup"><span data-stu-id="aea3b-127">The contract name is inferred from the contract type, which means that this export will match the previous import.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="aea3b-128">Exportações e importações geralmente devem ser declaradas em classes ou membros públicos.</span><span class="sxs-lookup"><span data-stu-id="aea3b-128">Exports and imports should usually be declared on public classes or members.</span></span> <span data-ttu-id="aea3b-129">É oferecido suporte a outras declarações, mas exportar ou importar um membro privado, protegido ou interno quebra o modelo de isolamento para a parte e, portanto, isso não é recomendado.</span><span class="sxs-lookup"><span data-stu-id="aea3b-129">Other declarations are supported, but exporting or importing a private, protected, or internal member breaks the isolation model for the part and is therefore not recommended.</span></span>  
  
 <span data-ttu-id="aea3b-130">O tipo de contrato deve corresponder exatamente para que a exportação e a importação sejam consideradas uma correspondência.</span><span class="sxs-lookup"><span data-stu-id="aea3b-130">The contract type must match exactly for the export and import to be considered a match.</span></span> <span data-ttu-id="aea3b-131">Considere a seguinte exportação.</span><span class="sxs-lookup"><span data-stu-id="aea3b-131">Consider the following export.</span></span>  
  
```vb  
<Export()> 'WILL NOT match the previous import!  
Public Class MyLogger  
    Implements IMyAddin  
  
End Class  
```  
  
```csharp  
[Export] //WILL NOT match the previous import!  
public class MyLogger : IMyAddin { }  
```  
  
 <span data-ttu-id="aea3b-132">Nessa exportação, o tipo de contrato é `MyLogger` ao invés de `IMyAddin`.</span><span class="sxs-lookup"><span data-stu-id="aea3b-132">In this export, the contract type is `MyLogger` instead of `IMyAddin`.</span></span> <span data-ttu-id="aea3b-133">Embora `MyLogger` implemente `IMyAddin` e, portanto, possa ser convertido em um objeto `IMyAddin`, essa exportação não corresponderá à importação anterior porque os tipos de contrato não são iguais.</span><span class="sxs-lookup"><span data-stu-id="aea3b-133">Even though `MyLogger` implements `IMyAddin`, and therefore could be cast to an `IMyAddin` object, this export will not match the previous import because the contract types are not the same.</span></span>  
  
 <span data-ttu-id="aea3b-134">Em geral, não é necessário especificar o nome do contrato, e a maioria dos contratos deve ser definida em relação ao tipo de contrato e metadados.</span><span class="sxs-lookup"><span data-stu-id="aea3b-134">In general, it is not necessary to specify the contract name, and most contracts should be defined in terms of the contract type and metadata.</span></span> <span data-ttu-id="aea3b-135">No entanto, em determinadas circunstâncias, é importante especificar o nome do contrato diretamente.</span><span class="sxs-lookup"><span data-stu-id="aea3b-135">However, under certain circumstances, it is important to specify the contract name directly.</span></span> <span data-ttu-id="aea3b-136">O caso mais comum é quando uma classe exporta vários valores que compartilham um tipo em comum, como primitivos.</span><span class="sxs-lookup"><span data-stu-id="aea3b-136">The most common case is when a class exports several values that share a common type, such as primitives.</span></span> <span data-ttu-id="aea3b-137">O nome do contrato pode ser especificado como primeiro parâmetro do atributo `Import` ou `Export`.</span><span class="sxs-lookup"><span data-stu-id="aea3b-137">The contract name can be specified as the first parameter of the `Import` or `Export` attribute.</span></span> <span data-ttu-id="aea3b-138">O código a seguir mostra uma importação e uma exportação com um nome de contrato especificado de `MajorRevision`.</span><span class="sxs-lookup"><span data-stu-id="aea3b-138">The following code shows an import and an export with a specified contract name of `MajorRevision`.</span></span>  
  
```vb  
Public Class MyExportClass  
  
    'This one will match  
    <Export("MajorRevision")>  
    Public ReadOnly Property MajorRevision As Integer  
        Get  
            Return 4  
        End Get  
    End Property  
  
    <Export("MinorRevision")>  
    Public ReadOnly Property MinorRevision As Integer  
        Get  
            Return 16  
        End Get  
    End Property  
End Class  
```  
  
```csharp  
public class MyClass  
{  
    [Import("MajorRevision")]  
    public int MajorRevision { get; set; }  
}  
  
public class MyExportClass  
{   
    [Export("MajorRevision")] //This one will match.  
    public int MajorRevision = 4;  
  
    [Export("MinorRevision")]  
    public int MinorRevision = 16;  
}  
```  
  
 <span data-ttu-id="aea3b-139">Se o tipo de contrato não for especificado, ele ainda será inferido do tipo da importação ou exportação.</span><span class="sxs-lookup"><span data-stu-id="aea3b-139">If the contract type is not specified, it will still be inferred from the type of the import or export.</span></span> <span data-ttu-id="aea3b-140">Entretanto, mesmo se o nome do contrato for especificado explicitamente, o tipo de contrato também deve corresponder exatamente para que a importação e a exportação sejam consideradas uma correspondência.</span><span class="sxs-lookup"><span data-stu-id="aea3b-140">However, even if the contract name is specified explicitly, the contract type must also match exactly for the import and export to be considered a match.</span></span> <span data-ttu-id="aea3b-141">Por exemplo, se o campo `MajorRevision` fosse uma cadeia de caracteres, os tipos de contrato inferidos não corresponderiam e a exportação não corresponderia à importação, apesar de ter o mesmo nome de contrato.</span><span class="sxs-lookup"><span data-stu-id="aea3b-141">For example, if the `MajorRevision` field was a string, the inferred contract types would not match and the export would not match the import, despite having the same contract name.</span></span>  
  
### <a name="importing-and-exporting-a-method"></a><span data-ttu-id="aea3b-142">Importando e exportando um método</span><span class="sxs-lookup"><span data-stu-id="aea3b-142">Importing and Exporting a Method</span></span>  
 <span data-ttu-id="aea3b-143">O atributo `Export` também pode decorar um método, da mesma maneira que uma classe, propriedade ou função.</span><span class="sxs-lookup"><span data-stu-id="aea3b-143">The `Export` attribute can also decorate a method, in the same way as a class, property, or function.</span></span> <span data-ttu-id="aea3b-144">Exportações de métodos devem especificar um tipo ou nome de contrato, uma vez que o tipo não pode ser inferido.</span><span class="sxs-lookup"><span data-stu-id="aea3b-144">Method exports must specify a contract type or contract name, as the type cannot be inferred.</span></span> <span data-ttu-id="aea3b-145">O tipo especificado pode ser um representante personalizado ou um tipo genérico, como `Func`.</span><span class="sxs-lookup"><span data-stu-id="aea3b-145">The specified type can be either a custom delegate or a generic type, such as `Func`.</span></span> <span data-ttu-id="aea3b-146">A classe a seguir exporta um método denominado `DoSomething`.</span><span class="sxs-lookup"><span data-stu-id="aea3b-146">The following class exports a method named `DoSomething`.</span></span>  
  
```vb  
Public Class MyAddin  
  
    'Explicitly specifying a generic type  
    <Export(GetType(Func(Of Integer, String)))>  
    Public Function DoSomething(ByVal TheParam As Integer) As String  
        Return Nothing 'Function body goes here  
    End Function  
  
End Class  
```  
  
```csharp  
public class MyAddin  
{  
    //Explicitly specifying a generic type.  
    [Export(typeof(Func<int, string>))]  
    public string DoSomething(int TheParam);  
}  
```  
  
 <span data-ttu-id="aea3b-147">Nessa classe, o método `DoSomething` considera um único parâmetro `int` e retorna um `string`.</span><span class="sxs-lookup"><span data-stu-id="aea3b-147">In this class, the `DoSomething` method takes a single `int` parameter and returns a `string`.</span></span> <span data-ttu-id="aea3b-148">Para corresponder a essa exportação, a parte da importação deve declarar um membro adequado.</span><span class="sxs-lookup"><span data-stu-id="aea3b-148">To match this export, the importing part must declare an appropriate member.</span></span> <span data-ttu-id="aea3b-149">A classe a seguir importa o método `DoSomething`.</span><span class="sxs-lookup"><span data-stu-id="aea3b-149">The following class imports the `DoSomething` method.</span></span>  
  
```vb  
Public Class MyClass1  
  
    'Contract name must match!  
    <Import()>  
    Public Property MajorRevision As Func(Of Integer, String)  
End Class  
```  
  
```csharp  
public class MyClass  
{  
    [Import] //Contract name must match!  
    public Func<int, string> DoSomething { get; set; }  
}  
```  
  
 <span data-ttu-id="aea3b-150">Para obter mais informações sobre como usar o objeto `Func<T, T>`, consulte <xref:System.Func%602>.</span><span class="sxs-lookup"><span data-stu-id="aea3b-150">For more information about how to use of the `Func<T, T>` object, see <xref:System.Func%602>.</span></span>  
  
<a name="types_of_imports"></a>   
## <a name="types-of-imports"></a><span data-ttu-id="aea3b-151">Tipos de importações</span><span class="sxs-lookup"><span data-stu-id="aea3b-151">Types of Imports</span></span>  
 <span data-ttu-id="aea3b-152">O MEF oferece suporte a vários tipos de importação, incluindo importação dinâmica, lenta, obrigatória e opcional.</span><span class="sxs-lookup"><span data-stu-id="aea3b-152">MEF support several import types, including dynamic, lazy, prerequisite, and optional.</span></span>  
  
### <a name="dynamic-imports"></a><span data-ttu-id="aea3b-153">Importações dinâmicas</span><span class="sxs-lookup"><span data-stu-id="aea3b-153">Dynamic Imports</span></span>  
 <span data-ttu-id="aea3b-154">Em alguns casos, a classe de importação pode querer corresponder exportações de qualquer tipo que tenham um nome de contrato específico.</span><span class="sxs-lookup"><span data-stu-id="aea3b-154">In some cases, the importing class may want to match exports of any type that have a particular contract name.</span></span> <span data-ttu-id="aea3b-155">Nesse cenário, a classe pode declarar uma *importação dinâmica*.</span><span class="sxs-lookup"><span data-stu-id="aea3b-155">In this scenario, the class can declare a *dynamic import*.</span></span> <span data-ttu-id="aea3b-156">A importação a seguir corresponde qualquer exportação com o nome de contrato "TheString".</span><span class="sxs-lookup"><span data-stu-id="aea3b-156">The following import matches any export with contract name "TheString".</span></span>  
  
```vb  
Public Class MyClass1  
  
    <Import("TheString")>  
    Public Property MyAddin  
  
End Class  
```  
  
```csharp  
public class MyClass  
{  
    [Import("TheString")]  
    public dynamic MyAddin { get; set; }  
}  
```  
  
 <span data-ttu-id="aea3b-157">Quando o tipo de contrato é inferido da palavra-chave `dynamic`, ele corresponderá a qualquer tipo de contrato.</span><span class="sxs-lookup"><span data-stu-id="aea3b-157">When the contract type is inferred from the `dynamic` keyword, it will match any contract type.</span></span> <span data-ttu-id="aea3b-158">Nesse caso, uma importação deve **sempre** especificar um nome de contrato para correspondência.</span><span class="sxs-lookup"><span data-stu-id="aea3b-158">In this case, an import should **always** specify a contract name to match on.</span></span> <span data-ttu-id="aea3b-159">(Se nenhum nome de contrato for especificado, será considerado que a importação não corresponde a nenhuma exportação.) As duas exportações a seguir corresponderiam à importação anterior.</span><span class="sxs-lookup"><span data-stu-id="aea3b-159">(If no contract name is specified, the import will be considered to match no exports.) Both of the following exports would match the previous import.</span></span>  
  
```vb  
<Export("TheString", GetType(IMyAddin))>  
Public Class MyLogger  
    Implements IMyAddin  
  
End Class  
  
<Export("TheString")>  
Public Class MyToolbar  
  
End Class  
```  
  
```csharp  
[Export("TheString", typeof(IMyAddin))]  
public class MyLogger : IMyAddin { }  
  
[Export("TheString")]  
public class MyToolbar { }  
```  
  
 <span data-ttu-id="aea3b-160">Obviamente, a classe de importação deve ser preparada para lidar com um objeto de tipo arbitrário.</span><span class="sxs-lookup"><span data-stu-id="aea3b-160">Obviously, the importing class must be prepared to deal with an object of arbitrary type.</span></span>  
  
### <a name="lazy-imports"></a><span data-ttu-id="aea3b-161">Importações lentas</span><span class="sxs-lookup"><span data-stu-id="aea3b-161">Lazy Imports</span></span>  
 <span data-ttu-id="aea3b-162">Em alguns casos, a classe de importação pode exigir uma referência indireta ao objeto importado, de modo que o objeto não seja instanciado imediatamente.</span><span class="sxs-lookup"><span data-stu-id="aea3b-162">In some cases, the importing class may require an indirect reference to the imported object, so that the object is not instantiated immediately.</span></span> <span data-ttu-id="aea3b-163">Nesse cenário, a classe pode declarar uma *importação lenta* usando o tipo de contrato `Lazy<T>`.</span><span class="sxs-lookup"><span data-stu-id="aea3b-163">In this scenario, the class can declare a *lazy import* by using a contract type of `Lazy<T>`.</span></span> <span data-ttu-id="aea3b-164">A propriedade de importação a seguir declara uma importação lenta.</span><span class="sxs-lookup"><span data-stu-id="aea3b-164">The following importing property declares a lazy import.</span></span>  
  
```vb  
Public Class MyClass1  
  
    <Import()>  
    Public Property MyAddin As Lazy(Of IMyAddin)  
  
End Class  
```  
  
```csharp  
public class MyClass  
{  
    [Import]  
    public Lazy<IMyAddin> MyAddin { get; set; }  
}  
```  
  
 <span data-ttu-id="aea3b-165">A partir do ponto de vista do mecanismo de composição, um tipo de contrato `Lazy<T>` é considerado idêntico ao tipo de contrato `T`.</span><span class="sxs-lookup"><span data-stu-id="aea3b-165">From the point of view of the composition engine, a contract type of `Lazy<T>` is considered identical to contract type of `T`.</span></span> <span data-ttu-id="aea3b-166">Portanto, a importação anterior corresponderia à exportação seguinte.</span><span class="sxs-lookup"><span data-stu-id="aea3b-166">Therefore, the previous import would match the following export.</span></span>  
  
```vb  
<Export(GetType(IMyAddin))>  
Public Class MyLogger  
    Implements IMyAddin  
  
End Class  
```  
  
```csharp  
[Export(typeof(IMyAddin))]  
public class MyLogger : IMyAddin { }  
```  
  
 <span data-ttu-id="aea3b-167">O nome e o tipo do contrato podem ser especificados no atributo `Import` para uma importação lenta, como descrito anteriormente na seção "Importações e exportações básicas".</span><span class="sxs-lookup"><span data-stu-id="aea3b-167">The contract name and contract type can be specified in the `Import` attribute for a lazy import, as described earlier in the "Basic Imports and Exports" section.</span></span>  
  
### <a name="prerequisite-imports"></a><span data-ttu-id="aea3b-168">Importações obrigatórias</span><span class="sxs-lookup"><span data-stu-id="aea3b-168">Prerequisite Imports</span></span>  
 <span data-ttu-id="aea3b-169">Partes de MEF exportadas geralmente são criadas pelo mecanismo de composição, em resposta a uma solicitação direta ou à necessidade de preencher uma importação correspondida.</span><span class="sxs-lookup"><span data-stu-id="aea3b-169">Exported MEF parts are typically created by the composition engine, in response to a direct request or the need to fill a matched import.</span></span> <span data-ttu-id="aea3b-170">Por padrão, ao criar uma parte, o mecanismo de composição usa o construtor sem parâmetro.</span><span class="sxs-lookup"><span data-stu-id="aea3b-170">By default, when creating a part, the composition engine uses the parameter-less constructor.</span></span> <span data-ttu-id="aea3b-171">Para fazer com que o mecanismo use um construtor diferente, você pode marcá-lo com o atributo `ImportingConstructor`.</span><span class="sxs-lookup"><span data-stu-id="aea3b-171">To make the engine use a different constructor, you can mark it with the `ImportingConstructor` attribute.</span></span>  
  
 <span data-ttu-id="aea3b-172">Cada parte pode ter somente um construtor para uso por parte do mecanismo de composição.</span><span class="sxs-lookup"><span data-stu-id="aea3b-172">Each part may have only one constructor for use by the composition engine.</span></span> <span data-ttu-id="aea3b-173">Não fornecer nenhum construtor padrão e nenhum atributo `ImportingConstructor`, ou fornecer mais de um atributo `ImportingConstructor`, gerará um erro.</span><span class="sxs-lookup"><span data-stu-id="aea3b-173">Providing no default constructor and no `ImportingConstructor` attribute, or providing more than one `ImportingConstructor` attribute, will produce an error.</span></span>  
  
 <span data-ttu-id="aea3b-174">Para preencher os parâmetros de um construtor marcado com o atributo `ImportingConstructor`, todos esses parâmetros são automaticamente declarados como importações.</span><span class="sxs-lookup"><span data-stu-id="aea3b-174">To fill the parameters of a constructor marked with the `ImportingConstructor` attribute, all of those parameters are automatically declared as imports.</span></span> <span data-ttu-id="aea3b-175">Essa é uma maneira conveniente de declarar importações que são usadas durante da inicialização da parte.</span><span class="sxs-lookup"><span data-stu-id="aea3b-175">This is a convenient way to declare imports that are used during part initialization.</span></span> <span data-ttu-id="aea3b-176">A classe a seguir usa `ImportingConstructor` para declarar uma importação.</span><span class="sxs-lookup"><span data-stu-id="aea3b-176">The following class uses `ImportingConstructor` to declare an import.</span></span>  
  
```vb  
Public Class MyClass1  
  
    Private _theAddin As IMyAddin  
  
    'Default constructor will NOT be used  
    'because the ImportingConstructor  
    'attribute is present.  
    Public Sub New()  
  
    End Sub  
  
    'This constructor will be used.  
    'An import with contract type IMyAddin  
    'is declared automatically.  
    <ImportingConstructor()>  
    Public Sub New(ByVal MyAddin As IMyAddin)  
        _theAddin = MyAddin  
    End Sub  
  
End Class  
```  
  
```csharp  
public class MyClass   
{  
    private IMyAddin _theAddin;  
  
    //Default constructor will NOT be  
    //used because the ImportingConstructor  
    //attribute is present.  
    public MyClass() { }  
  
    //This constructor will be used.  
    //An import with contract type IMyAddin is   
    //declared automatically.  
    [ImportingConstructor]   
    public MyClass(IMyAddin MyAddin)   
    {  
        _theAddin = MyAddin;  
    }  
}  
```  
  
 <span data-ttu-id="aea3b-177">Por padrão, o atributo `ImportingConstructor` usa tipos e nomes de contrato inferidos para todas as importações de parâmetros.</span><span class="sxs-lookup"><span data-stu-id="aea3b-177">By default, the `ImportingConstructor` attribute uses inferred contract types and contract names for all of the parameter imports.</span></span> <span data-ttu-id="aea3b-178">É impossível substituir isso decorando os parâmetros com atributos `Import`, que podem então definir o tipo e o nome do contrato explicitamente.</span><span class="sxs-lookup"><span data-stu-id="aea3b-178">It is possible to override this by decorating the parameters with `Import` attributes, which can then define the contract type and contract name explicitly.</span></span> <span data-ttu-id="aea3b-179">O código a seguir demonstra um construtor que usa essa sintaxe para importar uma classe derivada ao invés de uma classe pai.</span><span class="sxs-lookup"><span data-stu-id="aea3b-179">The following code demonstrates a constructor that uses this syntax to import a derived class instead of a parent class.</span></span>  
  
```vb  
<ImportingConstructor()>  
Public Sub New(<Import(GetType(IMySubAddin))> ByVal MyAddin As IMyAddin)  
  
End Sub  
```  
  
```csharp  
[ImportingConstructor]   
public MyClass([Import(typeof(IMySubAddin))]IMyAddin MyAddin)   
{  
    _theAddin = MyAddin;  
}  
```  
  
 <span data-ttu-id="aea3b-180">Em particular, você deve tomar cuidado com parâmetros de coleção.</span><span class="sxs-lookup"><span data-stu-id="aea3b-180">In particular, you should be careful with collection parameters.</span></span> <span data-ttu-id="aea3b-181">Por exemplo, se você especificar `ImportingConstructor` em um construtor com o parâmetro do tipo `IEnumerable<int>`, a importação corresponderá a uma única exportação do tipo `IEnumerable<int>`, ao invés de a um conjunto de exportações do tipo `int`.</span><span class="sxs-lookup"><span data-stu-id="aea3b-181">For example, if you specify `ImportingConstructor` on a constructor with a parameter of type `IEnumerable<int>`, the import will match a single export of type `IEnumerable<int>`, instead of a set of exports of type `int`.</span></span> <span data-ttu-id="aea3b-182">Para corresponder a um conjunto de exportações do tipo `int`, você precisa decorar o parâmetro com o atributo `ImportMany`.</span><span class="sxs-lookup"><span data-stu-id="aea3b-182">To match a set of exports of type `int`, you have to decorate the parameter with the `ImportMany` attribute.</span></span>  
  
 <span data-ttu-id="aea3b-183">Os parâmetros declarados como importações pelo atributo `ImportingConstructor` também são marcados como *importações de pré-requisito*.</span><span class="sxs-lookup"><span data-stu-id="aea3b-183">Parameters declared as imports by the `ImportingConstructor` attribute are also marked as *prerequisite imports*.</span></span> <span data-ttu-id="aea3b-184">O MEF normalmente permite exportações e importações para formar um *ciclo*.</span><span class="sxs-lookup"><span data-stu-id="aea3b-184">MEF normally allows exports and imports to form a *cycle*.</span></span> <span data-ttu-id="aea3b-185">Por exemplo, um ciclo é quando o objeto A importa o objeto B, que por sua vez importa o objeto A. Em circunstância normais, um ciclo não é um problema e o contêiner de composição constrói os dois objetos normalmente.</span><span class="sxs-lookup"><span data-stu-id="aea3b-185">For example, a cycle is where object A imports object B, which in turn imports object A. Under ordinary circumstances, a cycle is not a problem, and the composition container constructs both objects normally.</span></span>  
  
 <span data-ttu-id="aea3b-186">Quando um valor importado é solicitado pelo construtor de uma parte, esse objeto não pode participar de um ciclo.</span><span class="sxs-lookup"><span data-stu-id="aea3b-186">When an imported value is required by the constructor of a part, that object cannot participate in a cycle.</span></span> <span data-ttu-id="aea3b-187">Se o objeto A exigir que o objeto B seja construído antes que ele próprio possa ser construído, e o objeto B importar o objeto A, então será impossível resolver o ciclo e um erro de composição ocorrerá.</span><span class="sxs-lookup"><span data-stu-id="aea3b-187">If object A requires that object B be constructed before it can be constructed itself, and object B imports object A, then the cycle will be unable to resolve and a composition error will occur.</span></span> <span data-ttu-id="aea3b-188">Importações declaradas nos parâmetros do construtor são, portanto, importações obrigatórias, que devem ser preenchidas antes que qualquer exportação do objeto que as requer possa ser usada.</span><span class="sxs-lookup"><span data-stu-id="aea3b-188">Imports declared on constructor parameters are therefore prerequisite imports, which must all be filled before any of the exports from the object that requires them can be used.</span></span>  
  
### <a name="optional-imports"></a><span data-ttu-id="aea3b-189">Importações opcionais</span><span class="sxs-lookup"><span data-stu-id="aea3b-189">Optional Imports</span></span>  
 <span data-ttu-id="aea3b-190">O atributo `Import` especifica um requisito para a parte funcionar.</span><span class="sxs-lookup"><span data-stu-id="aea3b-190">The `Import` attribute specifies a requirement for the part to function.</span></span> <span data-ttu-id="aea3b-191">Se uma importação não puder ser atendida, a composição dessa parte falhará e a parte não estará disponível.</span><span class="sxs-lookup"><span data-stu-id="aea3b-191">If an import cannot be fulfilled, the composition of that part will fail and the part will not be available.</span></span>  
  
 <span data-ttu-id="aea3b-192">Você pode especificar que uma importação é *optional* usando a propriedade `AllowDefault`.</span><span class="sxs-lookup"><span data-stu-id="aea3b-192">You can specify that an import is *optional* by using the `AllowDefault` property.</span></span> <span data-ttu-id="aea3b-193">Nesse caso, a composição será bem-sucedida mesmo se a importação não corresponder a nenhuma exportação disponível, e a propriedade de importação será definida como o padrão em relação ao seu tipo de propriedade (`null` para propriedades de objeto, `false` para Booleanos ou zero para propriedades numéricas.) A classe a seguir usa uma importação opcional.</span><span class="sxs-lookup"><span data-stu-id="aea3b-193">In this case, the composition will succeed even if the import does not match any available exports, and the importing property will be set to the default for its property type (`null` for object properties, `false` for Booleans, or zero for numeric properties.) The following class uses an optional import.</span></span>  
  
```vb  
Public Class MyClass1  
  
    <Import(AllowDefault:=True)>  
    Public Property thePlugin As Plugin  
  
    'If no matching export is available,  
    'thePlugin will be set to null.  
End Class  
```  
  
```csharp  
public class MyClass  
{  
    [Import(AllowDefault = true)]  
    public Plugin thePlugin { get; set; }  
  
    //If no matching export is avaliable,  
    //thePlugin will be set to null.  
}  
```  
  
### <a name="importing-multiple-objects"></a><span data-ttu-id="aea3b-194">Importando vários objetos</span><span class="sxs-lookup"><span data-stu-id="aea3b-194">Importing Multiple Objects</span></span>  
 <span data-ttu-id="aea3b-195">O atributo `Import` só será composto com êxito quando ele corresponder a somente uma exportação.</span><span class="sxs-lookup"><span data-stu-id="aea3b-195">The `Import` attribute will only be successfully composed when it matches one and only one export.</span></span> <span data-ttu-id="aea3b-196">Outros casos produzirão um erro de composição.</span><span class="sxs-lookup"><span data-stu-id="aea3b-196">Other cases will produce a composition error.</span></span> <span data-ttu-id="aea3b-197">Para importar mais de uma exportação que corresponda ao mesmo contrato, use o atributo `ImportMany`.</span><span class="sxs-lookup"><span data-stu-id="aea3b-197">To import more than one export that matches the same contract, use the `ImportMany` attribute.</span></span> <span data-ttu-id="aea3b-198">Importações marcadas com esse atributo são sempre opcionais.</span><span class="sxs-lookup"><span data-stu-id="aea3b-198">Imports marked with this attribute are always optional.</span></span> <span data-ttu-id="aea3b-199">Por exemplo, a composição não falhará se nenhuma exportação correspondente estiver presente.</span><span class="sxs-lookup"><span data-stu-id="aea3b-199">For example, composition will not fail if no matching exports are present.</span></span> <span data-ttu-id="aea3b-200">A classe a seguir importa qualquer número de exportações do tipo `IMyAddin`.</span><span class="sxs-lookup"><span data-stu-id="aea3b-200">The following class imports any number of exports of type `IMyAddin`.</span></span>  
  
```vb  
Public Class MyClass1  
  
    <ImportMany()>  
    Public Property MyAddin As IEnumerable(Of IMyAddin)  
  
End Class  
```  
  
```csharp  
public class MyClass  
{  
    [ImportMany]  
    public IEnumerable<IMyAddin> MyAddin { get; set; }  
}  
```  
  
 <span data-ttu-id="aea3b-201">A matriz importada pode ser acessada usando sintaxe e métodos comuns `IEnumerable<T>`.</span><span class="sxs-lookup"><span data-stu-id="aea3b-201">The imported array can be accessed by using ordinary `IEnumerable<T>` syntax and methods.</span></span> <span data-ttu-id="aea3b-202">Também é impossível usar uma matriz comum (`IMyAddin[]`).</span><span class="sxs-lookup"><span data-stu-id="aea3b-202">It is also possible to use an ordinary array (`IMyAddin[]`) instead.</span></span>  
  
 <span data-ttu-id="aea3b-203">O padrão pode ser bastante importante quando usado combinado à sintaxe `Lazy<T>`.</span><span class="sxs-lookup"><span data-stu-id="aea3b-203">This pattern can be very important when you use it in combination with the `Lazy<T>` syntax.</span></span> <span data-ttu-id="aea3b-204">Por exemplo, ao usar `ImportMany`, `IEnumerable<T>` e `Lazy<T>`, você pode importar referências indiretas a qualquer número de objetos e apenas instanciar aqueles que são necessários.</span><span class="sxs-lookup"><span data-stu-id="aea3b-204">For example, by using `ImportMany`, `IEnumerable<T>`, and `Lazy<T>`, you can import indirect references to any number of objects and only instantiate the ones that become necessary.</span></span> <span data-ttu-id="aea3b-205">A classe a seguir mostra esse padrão.</span><span class="sxs-lookup"><span data-stu-id="aea3b-205">The following class shows this pattern.</span></span>  
  
```vb  
Public Class MyClass1  
  
    <ImportMany()>  
    Public Property MyAddin As IEnumerable(Of Lazy(Of IMyAddin))  
  
End Class  
```  
  
```csharp  
public class MyClass  
{  
    [ImportMany]  
    public IEnumerable<Lazy<IMyAddin>> MyAddin { get; set; }  
}  
```  
  
<a name="avoiding_discovery"></a>   
## <a name="avoiding-discovery"></a><span data-ttu-id="aea3b-206">Evitando descobertas</span><span class="sxs-lookup"><span data-stu-id="aea3b-206">Avoiding Discovery</span></span>  
 <span data-ttu-id="aea3b-207">Em alguns casos, talvez você queira impedir que uma parte seja descoberta como parte de um catálogo.</span><span class="sxs-lookup"><span data-stu-id="aea3b-207">In some cases, you may want to prevent a part from being discovered as part of a catalog.</span></span> <span data-ttu-id="aea3b-208">Por exemplo, a parte pode ser uma classe base para fins de herança, mas não para ser usada.</span><span class="sxs-lookup"><span data-stu-id="aea3b-208">For example, the part may be a base class intended to be inherited from, but not used.</span></span> <span data-ttu-id="aea3b-209">Há duas maneiras de fazer isso.</span><span class="sxs-lookup"><span data-stu-id="aea3b-209">There are two ways to accomplish this.</span></span> <span data-ttu-id="aea3b-210">Primeiramente, você pode usar a palavra-chave `abstract` na classe da parte.</span><span class="sxs-lookup"><span data-stu-id="aea3b-210">First, you can use the `abstract` keyword on the part class.</span></span> <span data-ttu-id="aea3b-211">Classes abstratas nunca oferecem exportações, embora possam fornecer exportações herdadas a classes derivadas.</span><span class="sxs-lookup"><span data-stu-id="aea3b-211">Abstract classes never provide exports, although they can provide inherited exports to classes that derive from them.</span></span>  
  
 <span data-ttu-id="aea3b-212">Se a classe não puder se tornar abstrata, você poderá decorá-la com o atributo `PartNotDiscoverable`.</span><span class="sxs-lookup"><span data-stu-id="aea3b-212">If the class cannot be made abstract, you can decorate it with the `PartNotDiscoverable` attribute.</span></span> <span data-ttu-id="aea3b-213">Uma parte decorada com esse atributo não será incluída em nenhum catálogo.</span><span class="sxs-lookup"><span data-stu-id="aea3b-213">A part decorated with this attribute will not be included in any catalogs.</span></span> <span data-ttu-id="aea3b-214">O exemplo a seguir demonstra esses padrões.</span><span class="sxs-lookup"><span data-stu-id="aea3b-214">The following example demonstrates these patterns.</span></span> <span data-ttu-id="aea3b-215">`DataOne` será descoberto pelo catálogo.</span><span class="sxs-lookup"><span data-stu-id="aea3b-215">`DataOne` will be discovered by the catalog.</span></span> <span data-ttu-id="aea3b-216">Uma vez que `DataTwo` é abstrato, ele não será descoberto.</span><span class="sxs-lookup"><span data-stu-id="aea3b-216">Since `DataTwo` is abstract, it will not be discovered.</span></span> <span data-ttu-id="aea3b-217">Uma vez que `DataThree` usou o atributo `PartNotDiscoverable`, ele não será descoberto.</span><span class="sxs-lookup"><span data-stu-id="aea3b-217">Since `DataThree` used the `PartNotDiscoverable` attribute, it will not be discovered.</span></span>  
  
```vb  
<Export()>  
Public Class DataOne  
    'This part will be discovered   
    'as normal by the catalog.  
End Class  
  
<Export()>  
Public MustInherit Class DataTwo  
    'This part will not be discovered  
    'by the catalog.  
End Class  
  
<PartNotDiscoverable()>  
<Export()>  
Public Class DataThree  
    'This part will also not be discovered  
    'by the catalog.  
End Class  
```  
  
```csharp  
[Export]  
public class DataOne  
{  
    //This part will be discovered  
    //as normal by the catalog.  
}  
  
[Export]  
public abstract class DataTwo  
{  
    //This part will not be discovered  
    //by the catalog.  
}  
  
[PartNotDiscoverable]  
[Export]  
public class DataThree  
{  
    //This part will also not be discovered  
    //by the catalog.  
}  
```  
  
<a name="metadata_and_metadata_views"></a>   
## <a name="metadata-and-metadata-views"></a><span data-ttu-id="aea3b-218">Metadados e exibições de metadados</span><span class="sxs-lookup"><span data-stu-id="aea3b-218">Metadata and Metadata Views</span></span>  
 <span data-ttu-id="aea3b-219">As exportações podem fornecer informações adicionais sobre elas mesmas, conhecidas como *metadados*.</span><span class="sxs-lookup"><span data-stu-id="aea3b-219">Exports can provide additional information about themselves known as *metadata*.</span></span> <span data-ttu-id="aea3b-220">Metadados podem ser usados para transmitir propriedades do objeto exportado à parte que realizará a importação.</span><span class="sxs-lookup"><span data-stu-id="aea3b-220">Metadata can be used to convey properties of the exported object to the importing part.</span></span> <span data-ttu-id="aea3b-221">A parte que realizará a importação pode usar esses dados para decidir quais exportações utilizar, ou coletar informações sobre uma exportação sem precisar construí-la.</span><span class="sxs-lookup"><span data-stu-id="aea3b-221">The importing part can use this data to decide which exports to use, or to gather information about an export without having to construct it.</span></span> <span data-ttu-id="aea3b-222">Por esse motivo, uma importação deve ser lenta para usar metadados.</span><span class="sxs-lookup"><span data-stu-id="aea3b-222">For this reason, an import must be lazy to use metadata.</span></span>  
  
 <span data-ttu-id="aea3b-223">Para usar metadados, geralmente você declara uma interface conhecida como *exibição de metadados*, que declara quais metadados estarão disponíveis.</span><span class="sxs-lookup"><span data-stu-id="aea3b-223">To use metadata, you typically declare an interface known as a *metadata view*, which declares what metadata will be available.</span></span> <span data-ttu-id="aea3b-224">A interface de exibição de metadados deve conter somente propriedades, e essas propriedades devem ter acessadores `get`.</span><span class="sxs-lookup"><span data-stu-id="aea3b-224">The metadata view interface must have only properties, and those properties must have `get` accessors.</span></span> <span data-ttu-id="aea3b-225">A interface a seguir é um exemplo de exibição de metadados.</span><span class="sxs-lookup"><span data-stu-id="aea3b-225">The following interface is an example metadata view.</span></span>  
  
```vb  
Public Interface IPluginMetadata  
  
    ReadOnly Property Name As String  
  
    <DefaultValue(1)>  
    ReadOnly Property Version As Integer  
  
End Interface  
```  
  
```csharp  
public interface IPluginMetadata  
{  
    string Name { get; }  
  
    [DefaultValue(1)]    
    int Version { get; }  
}  
```  
  
 <span data-ttu-id="aea3b-226">Também é possível usar uma coleção genérica, `IDictionary<string, object>`, como uma exibição de metadados, mas isso não inclui os benefícios da verificação de tipo e deve ser evitado.</span><span class="sxs-lookup"><span data-stu-id="aea3b-226">It is also possible to use a generic collection, `IDictionary<string, object>`, as a metadata view, but this forfeits the benefits of type checking and should be avoided.</span></span>  
  
 <span data-ttu-id="aea3b-227">Normalmente, todas as propriedades denominadas na exibição de metadados são necessárias, e qualquer exportação que não as forneça não será considerada correspondente.</span><span class="sxs-lookup"><span data-stu-id="aea3b-227">Ordinarily, all of the properties named in the metadata view are required, and any exports that do not provide them will not be considered a match.</span></span> <span data-ttu-id="aea3b-228">O atributo `DefaultValue` especifica que uma propriedade é opcional.</span><span class="sxs-lookup"><span data-stu-id="aea3b-228">The `DefaultValue` attribute specifies that a property is optional.</span></span> <span data-ttu-id="aea3b-229">Se a propriedade não for incluída, o valor padrão especificado como parâmetro de `DefaultValue` será atribuído a ela.</span><span class="sxs-lookup"><span data-stu-id="aea3b-229">If the property is not included, it will be assigned the default value specified as a parameter of `DefaultValue`.</span></span> <span data-ttu-id="aea3b-230">A seguir, há duas classes diferentes decoradas com metadados.</span><span class="sxs-lookup"><span data-stu-id="aea3b-230">The following are two different classes decorated with metadata.</span></span> <span data-ttu-id="aea3b-231">Essas duas classes corresponderiam à exibição de metadados anterior.</span><span class="sxs-lookup"><span data-stu-id="aea3b-231">Both of these classes would match the previous metadata view.</span></span>  
  
```vb  
<Export(GetType(IPlugin))>  
<ExportMetadata("Name", "Logger")>  
<ExportMetadata("Version", 4)>  
Public Class MyLogger  
    Implements IPlugin  
  
End Class  
  
'Version is not required because of the DefaultValue  
<Export(GetType(IPlugin))>  
<ExportMetadata("Name", "Disk Writer")>  
Public Class DWriter  
    Implements IPlugin  
  
End Class  
```  
  
```csharp  
[Export(typeof(IPlugin)),  
    ExportMetadata("Name", "Logger"),  
    ExportMetadata("Version", 4)]  
public class Logger : IPlugin  
{  
}  
  
[Export(typeof(IPlugin)),  
    ExportMetadata("Name", "Disk Writer")]   
    //Version is not required because of the DefaultValue  
public class DWriter : IPlugin  
{  
}  
```  
  
 <span data-ttu-id="aea3b-232">Os metadados são expressados após o atributo `Export` usando o atributo `ExportMetadata`.</span><span class="sxs-lookup"><span data-stu-id="aea3b-232">Metadata is expressed after the `Export` attribute by using the `ExportMetadata` attribute.</span></span> <span data-ttu-id="aea3b-233">Cada metadado é composto de um par de nome/valor.</span><span class="sxs-lookup"><span data-stu-id="aea3b-233">Each piece of metadata is composed of a name/value pair.</span></span> <span data-ttu-id="aea3b-234">A parte do nome dos metadados deve corresponder ao nome da propriedade adequada na exibição de metadados, e o valor será atribuído a essa propriedade.</span><span class="sxs-lookup"><span data-stu-id="aea3b-234">The name portion of the metadata must match the name of the appropriate property in the metadata view, and the value will be assigned to that property.</span></span>  
  
 <span data-ttu-id="aea3b-235">É o importador que especifica qual exibição de metadados será usada, se houver.</span><span class="sxs-lookup"><span data-stu-id="aea3b-235">It is the importer that specifies what metadata view, if any, will be in use.</span></span> <span data-ttu-id="aea3b-236">Uma importação com metadados é declarada como uma importação lenta, com a interface dos metadados como o segundo parâmetro de tipo para `Lazy<T,T>`.</span><span class="sxs-lookup"><span data-stu-id="aea3b-236">An import with metadata is declared as a lazy import, with the metadata interface as the second type parameter to `Lazy<T,T>`.</span></span> <span data-ttu-id="aea3b-237">A classe a seguir importa a parte anterior com os metadados.</span><span class="sxs-lookup"><span data-stu-id="aea3b-237">The following class imports the previous part with metadata.</span></span>  
  
```vb  
Public Class Addin  
  
    <Import()>  
    Public Property plugin As Lazy(Of IPlugin, IPluginMetadata)  
End Class  
```  
  
```csharp  
public class Addin  
{  
    [Import]  
    public Lazy<IPlugin, IPluginMetadata> plugin;  
}  
```  
  
 <span data-ttu-id="aea3b-238">Em muitos casos, você vai querer combinar metadados com o atributo `ImportMany`, a fim de analisar as importações disponíveis, escolher e instanciar apenas uma ou filtrar uma coleção para corresponder a uma condição específica.</span><span class="sxs-lookup"><span data-stu-id="aea3b-238">In many cases, you will want to combine metadata with the `ImportMany` attribute, in order to parse through the available imports and choose and instantiate only one, or filter a collection to match a certain condition.</span></span> <span data-ttu-id="aea3b-239">A classe a seguir instancia somente `IPlugin` objetos que possuem o valor `Name` "Agente".</span><span class="sxs-lookup"><span data-stu-id="aea3b-239">The following class instantiates only `IPlugin` objects that have the `Name` value "Logger".</span></span>  
  
```vb  
Public Class User  
  
    <ImportMany()>  
    Public Property plugins As IEnumerable(Of Lazy(Of IPlugin, IPluginMetadata))  
  
    Public Function InstantiateLogger() As IPlugin  
  
        Dim logger As IPlugin  
        logger = Nothing  
  
        For Each Plugin As Lazy(Of IPlugin, IPluginMetadata) In plugins  
            If (Plugin.Metadata.Name = "Logger") Then  
                logger = Plugin.Value  
            End If  
        Next  
        Return logger  
    End Function  
  
End Class  
```  
  
```csharp  
public class User  
{  
    [ImportMany]  
    public IEnumerable<Lazy<IPlugin, IPluginMetadata>> plugins;  
  
    public IPlugin InstantiateLogger ()  
    {  
        IPlugin logger = null;  
  
        foreach (Lazy<IPlugin, IPluginMetadata> plugin in plugins)  
        {  
            if (plugin.Metadata.Name = "Logger") logger = plugin.Value;  
        }  
        return logger;  
    }  
}  
```  
  
<a name="import_and_export_inheritance"></a>   
## <a name="import-and-export-inheritance"></a><span data-ttu-id="aea3b-240">Herança de importações e exportações</span><span class="sxs-lookup"><span data-stu-id="aea3b-240">Import and Export Inheritance</span></span>  
 <span data-ttu-id="aea3b-241">Se uma classe herdar de uma parte, essa classe também pode se tornar uma parte.</span><span class="sxs-lookup"><span data-stu-id="aea3b-241">If a class inherits from a part, that class may also become a part.</span></span> <span data-ttu-id="aea3b-242">As importações são sempre herdadas por subclasses.</span><span class="sxs-lookup"><span data-stu-id="aea3b-242">Imports are always inherited by subclasses.</span></span> <span data-ttu-id="aea3b-243">Portanto, uma subclasse de uma parte sempre será uma parte, com as mesmas importações que sua classe pai.</span><span class="sxs-lookup"><span data-stu-id="aea3b-243">Therefore, a subclass of a part will always be a part, with the same imports as its parent class.</span></span>  
  
 <span data-ttu-id="aea3b-244">Exportações declaradas usando o atributo `Export` não são herdadas por subclasses.</span><span class="sxs-lookup"><span data-stu-id="aea3b-244">Exports declared by using the `Export` attribute are not inherited by subclasses.</span></span> <span data-ttu-id="aea3b-245">Entretanto, uma parte pode exportar a si mesma usando o atributo `InheritedExport`.</span><span class="sxs-lookup"><span data-stu-id="aea3b-245">However, a part can export itself by using the `InheritedExport` attribute.</span></span> <span data-ttu-id="aea3b-246">Subclasses da parte herdarão e fornecerão a mesma exportação, incluindo o nome e o tipo do contrato.</span><span class="sxs-lookup"><span data-stu-id="aea3b-246">Subclasses of the part will inherit and provide the same export, including contract name and contract type.</span></span> <span data-ttu-id="aea3b-247">Diferentemente de um atributo `Export`, `InheritedExport` pode ser aplicado somente no nível da classe e não no nível do membro.</span><span class="sxs-lookup"><span data-stu-id="aea3b-247">Unlike an `Export` attribute, `InheritedExport` can be applied only at the class level, and not at the member level.</span></span> <span data-ttu-id="aea3b-248">Portanto, exportações no nível do membro nunca podem ser herdadas.</span><span class="sxs-lookup"><span data-stu-id="aea3b-248">Therefore, member-level exports can never be inherited.</span></span>  
  
 <span data-ttu-id="aea3b-249">As quatro classes a seguir demonstram os princípios da herança de importação e exportação.</span><span class="sxs-lookup"><span data-stu-id="aea3b-249">The following four classes demonstrate the principles of import and export inheritance.</span></span> <span data-ttu-id="aea3b-250">A `NumTwo` é herdada da `NumOne`, portanto a `NumTwo` importará a `IMyData`.</span><span class="sxs-lookup"><span data-stu-id="aea3b-250">`NumTwo` inherits from `NumOne`, so `NumTwo` will import `IMyData`.</span></span> <span data-ttu-id="aea3b-251">Exportações comuns não são herdadas, por isso, `NumTwo` não exportará nada.</span><span class="sxs-lookup"><span data-stu-id="aea3b-251">Ordinary exports are not inherited, so `NumTwo` will not export anything.</span></span> <span data-ttu-id="aea3b-252">`NumFour` herda de `NumThree`.</span><span class="sxs-lookup"><span data-stu-id="aea3b-252">`NumFour` inherits from `NumThree`.</span></span> <span data-ttu-id="aea3b-253">Como `NumThree` usou `InheritedExport`, `NumFour` tem uma exportação com o tipo de contrato `NumThree`.</span><span class="sxs-lookup"><span data-stu-id="aea3b-253">Because `NumThree` used `InheritedExport`, `NumFour` has one export with contract type `NumThree`.</span></span> <span data-ttu-id="aea3b-254">Exportações no nível do membro nunca são herdadas, portanto, `IMyData` não é exportado.</span><span class="sxs-lookup"><span data-stu-id="aea3b-254">Member-level exports are never inherited, so `IMyData` is not exported.</span></span>  
  
```vb  
<Export()>  
Public Class NumOne  
    <Import()>  
    Public Property MyData As IMyData  
End Class  
  
Public Class NumTwo  
    Inherits NumOne  
  
    'Imports are always inherited, so NumTwo will  
    'Import IMyData  
  
    'Ordinary exports are not inherited, so  
    'NumTwo will NOT export anything.  As a result it  
    'will not be discovered by the catalog!  
  
End Class  
  
<InheritedExport()>  
Public Class NumThree  
  
    <Export()>  
    Public Property MyData As IMyData  
  
    'This part provides two exports, one of  
    'contract type NumThree, and one of   
    'contract type IMyData.  
  
End Class  
  
Public Class NumFour  
    Inherits NumThree  
  
    'Because NumThree used InheritedExport,  
    'this part has one export with contract   
    'type NumThree.  
  
    'Member-level exports are never inherited,  
    'so IMyData is not exported.  
  
End Class  
```  
  
```csharp  
[Export]  
public class NumOne  
{  
    [Import]  
    public IMyData MyData { get; set; }  
}  
  
public class NumTwo : NumOne  
{  
    //Imports are always inherited, so NumTwo will   
    //import IMyData.  
  
    //Ordinary exports are not inherited, so   
    //NumTwo will NOT export anything. As a result it   
    //will not be discovered by the catalog!  
}  
  
[InheritedExport]  
public class NumThree  
{  
    [Export]  
    Public IMyData MyData { get; set; }  
  
    //This part provides two exports, one of  
    //contract type NumThree, and one of  
    //contract type IMyData.  
}  
  
public class NumFour : NumThree  
{  
    //Because NumThree used InheritedExport,  
    //this part has one export with contract  
    //type NumThree.  
  
    //Member-level exports are never inherited,  
    //so IMyData is not exported.  
}  
```  
  
 <span data-ttu-id="aea3b-255">Se houver metadados associados a um atributo `InheritedExport`, esses metadados também serão herdados.</span><span class="sxs-lookup"><span data-stu-id="aea3b-255">If there is metadata associated with an `InheritedExport` attribute, that metadata will also be inherited.</span></span> <span data-ttu-id="aea3b-256">(Para obter mais informações, consulte a seção anterior "Metadados e exibições de metadados".) Metadados herdados não podem ser modificados pela subclasse.</span><span class="sxs-lookup"><span data-stu-id="aea3b-256">(For more information, see the earlier "Metadata and Metadata Views" section.) Inherited metadata cannot be modified by the subclass.</span></span> <span data-ttu-id="aea3b-257">No entanto, ao declarar novamente o atributo `InheritedExport` com o mesmo nome e tipo de contrato, mas com novos metadados, a subclasse pode substituir os metadados herdados por novos metadados.</span><span class="sxs-lookup"><span data-stu-id="aea3b-257">However, by re-declaring the `InheritedExport` attribute with the same contract name and contract type, but with new metadata, the subclass can replace the inherited metadata with new metadata.</span></span> <span data-ttu-id="aea3b-258">A classe a seguir demonstra esse princípio.</span><span class="sxs-lookup"><span data-stu-id="aea3b-258">The following class demonstrates this principle.</span></span> <span data-ttu-id="aea3b-259">A parte `MegaLogger` herda de `Logger` e inclui o atributo `InheritedExport`.</span><span class="sxs-lookup"><span data-stu-id="aea3b-259">The `MegaLogger` part inherits from `Logger` and includes the `InheritedExport` attribute.</span></span> <span data-ttu-id="aea3b-260">Uma vez que `MegaLogger` declara novamente novos metadados nomeados como Status, ele não herda os metadados de Nome e Versão de `Logger`.</span><span class="sxs-lookup"><span data-stu-id="aea3b-260">Since `MegaLogger` re-declares new metadata named Status, it does not inherit the Name and Version metadata from `Logger`.</span></span>  
  
```vb  
<InheritedExport(GetType(IPlugin))>  
<ExportMetadata("Name", "Logger")>  
<ExportMetadata("Version", 4)>  
Public Class Logger  
    Implements IPlugin  
  
    'Exports with contract type IPlugin  
    'and metadata "Name" and "Version".  
End Class  
  
Public Class SuperLogger  
    Inherits Logger  
  
    'Exports with contract type IPlugin and   
    'metadata "Name" and "Version", exactly the same  
    'as the Logger class.  
  
End Class  
  
<InheritedExport(GetType(IPlugin))>  
<ExportMetadata("Status", "Green")>  
Public Class MegaLogger  
    Inherits Logger  
  
    'Exports with contract type IPlugin and   
    'metadata "Status" only. Re-declaring   
    'the attribute replaces all metadata.  
  
End Class  
```  
  
```csharp  
[InheritedExport(typeof(IPlugin)),  
    ExportMetadata("Name", "Logger"),  
    ExportMetadata("Version", 4)]  
public class Logger : IPlugin  
{  
    //Exports with contract type IPlugin and   
    //metadata "Name" and "Version".  
}  
  
public class SuperLogger : Logger  
{  
    //Exports with contract type IPlugin and   
    //metadata "Name" and "Version", exactly the same  
    //as the Logger class.  
}  
  
[InheritedExport(typeof(IPlugin)),  
    ExportMetadata("Status", "Green")]  
public class MegaLogger : Logger        {  
    //Exports with contract type IPlugin and   
    //metadata "Status" only. Re-declaring   
    //the attribute replaces all metadata.  
}  
```  
  
 <span data-ttu-id="aea3b-261">Ao declarar novamente o atributo `InheritedExport` para substituir metadados, assegure-se de que os tipos de contrato sejam iguais.</span><span class="sxs-lookup"><span data-stu-id="aea3b-261">When re-declaring the `InheritedExport` attribute to override metadata, make sure that the contract types are the same.</span></span> <span data-ttu-id="aea3b-262">(No exemplo anterior, `IPlugin` é o tipo de contrato.) Caso sejam diferentes, ao invés da substituição, o segundo atributo criará uma segunda exportação independente da parte.</span><span class="sxs-lookup"><span data-stu-id="aea3b-262">(In the previous example, `IPlugin` is the contract type.) If they differ, instead of overriding, the second attribute will create a second, independent export from the part.</span></span> <span data-ttu-id="aea3b-263">Em geral, isso significa que você terá que especificar explicitamente o tipo de contrato ao substituir um atributo `InheritedExport`, como mostrado no exemplo anterior.</span><span class="sxs-lookup"><span data-stu-id="aea3b-263">Generally, this means that you will have to explicitly specify the contract type when you override an `InheritedExport` attribute, as shown in the previous example.</span></span>  
  
 <span data-ttu-id="aea3b-264">Uma vez que interfaces não podem ser instanciadas diretamente, elas geralmente não podem ser decoradas com atributos `Export` ou `Import`.</span><span class="sxs-lookup"><span data-stu-id="aea3b-264">Since interfaces cannot be instantiated directly, they generally cannot be decorated with `Export` or `Import` attributes.</span></span> <span data-ttu-id="aea3b-265">No entanto, uma interface pode ser decorada com um atributo `InheritedExport` no nível da interface, e essa exportação, juntamente com quaisquer metadados associados, serão herdados por qualquer classe de implementação.</span><span class="sxs-lookup"><span data-stu-id="aea3b-265">However, an interface can be decorated with an `InheritedExport` attribute at the interface level, and that export along with any associated metadata will be inherited by any implementing classes.</span></span> <span data-ttu-id="aea3b-266">Entretanto, a interface em si não estará disponível como uma parte.</span><span class="sxs-lookup"><span data-stu-id="aea3b-266">The interface itself will not be available as a part, however.</span></span>  
  
<a name="custom_export_attributes"></a>   
## <a name="custom-export-attributes"></a><span data-ttu-id="aea3b-267">Atributos de exportação personalizados</span><span class="sxs-lookup"><span data-stu-id="aea3b-267">Custom Export Attributes</span></span>  
 <span data-ttu-id="aea3b-268">Os atributos de exportação básicos, `Export` e `InheritedExport`, podem ser estendidos para incluir metadados como propriedades de atributo.</span><span class="sxs-lookup"><span data-stu-id="aea3b-268">The basic export attributes, `Export` and `InheritedExport`, can be extended to include metadata as attribute properties.</span></span> <span data-ttu-id="aea3b-269">Essa técnica é útil para aplicar metadados semelhantes a diversas partes ou criar uma árvore de herança de atributos de metadados.</span><span class="sxs-lookup"><span data-stu-id="aea3b-269">This technique is useful for applying similar metadata to many parts, or creating an inheritance tree of metadata attributes.</span></span>  
  
 <span data-ttu-id="aea3b-270">Um atributo personalizado pode especificar o tipo de contrato, o nome do contrato ou qualquer outro metadado.</span><span class="sxs-lookup"><span data-stu-id="aea3b-270">A custom attribute can specify the contract type, the contract name, or any other metadata.</span></span> <span data-ttu-id="aea3b-271">Para definir um atributo personalizado, uma classe que herda de `ExportAttribute` (ou `InheritedExportAttribute`) deve ser declarada com o atributo `MetadataAttribute`.</span><span class="sxs-lookup"><span data-stu-id="aea3b-271">In order to define a custom attribute, a class inheriting from `ExportAttribute` (or `InheritedExportAttribute`) must be decorated with the `MetadataAttribute` attribute.</span></span> <span data-ttu-id="aea3b-272">A classe a seguir define um atributo personalizado.</span><span class="sxs-lookup"><span data-stu-id="aea3b-272">The following class defines a custom attribute.</span></span>  
  
```vb  
<MetadataAttribute()>  
<AttributeUsage(AttributeTargets.Class, AllowMultiple:=false)>  
Public Class MyAttribute  
    Inherits ExportAttribute  
  
    Public Property MyMetadata As String  
  
    Public Sub New(ByVal myMetadata As String)  
        MyBase.New(GetType(IMyAddin))  
  
        myMetadata = myMetadata  
    End Sub  
  
End Class  
```  
  
```csharp  
[MetadataAttribute]  
[AttributeUsage(AttributeTargets.Class, AllowMultiple=false)]  
public class MyAttribute : ExportAttribute  
{  
    public MyAttribute(string myMetadata)   
        : base(typeof(IMyAddin))  
    {  
        MyMetadata = myMetadata;  
    }  
  
    public string MyMetadata { get; private set; }  
}  
```  
  
 <span data-ttu-id="aea3b-273">Essa classe define um atributo personalizado denominado `MyAttribute` com o tipo de contrato `IMyData` e alguns metadados denominados `MyMetadata`.</span><span class="sxs-lookup"><span data-stu-id="aea3b-273">This class defines a custom attribute named `MyAttribute` with contract type `IMyData` and some metadata named `MyMetadata`.</span></span> <span data-ttu-id="aea3b-274">Todas as propriedades em uma classe marcada com o atributo `MetadataAttribute` são consideradas como sendo metadados definidos no atributo personalizado.</span><span class="sxs-lookup"><span data-stu-id="aea3b-274">All properties in a class marked with the `MetadataAttribute` attribute are considered to be metadata defined in the custom attribute.</span></span> <span data-ttu-id="aea3b-275">As duas declarações a seguir são equivalentes.</span><span class="sxs-lookup"><span data-stu-id="aea3b-275">The following two declarations are equivalent.</span></span>  
  
```vb  
<Export(GetType(IMyAddin))>  
<ExportMetadata("MyMetadata", "theData")>  
Public Property myAddin As MyAddin  
  
<MyAttribute("theData")>  
Public Property myAddin As MyAddin  
```  
  
```csharp  
[Export(typeof(IMyAddin)),   
    ExportMetadata("MyMetadata", "theData")]  
public MyAddin myAddin { get; set; }  
```  
  
```  
[MyAttribute("theData")]  
public MyAddin myAddin { get; set; }  
```  
  
 <span data-ttu-id="aea3b-276">Na primeira declaração, o tipo de contrato e os metadados são definidos explicitamente.</span><span class="sxs-lookup"><span data-stu-id="aea3b-276">In the first declaration, the contract type and metadata are explicitly defined.</span></span> <span data-ttu-id="aea3b-277">Na segunda declaração, o tipo de contrato e os metadados são implícitos no atributo personalizado.</span><span class="sxs-lookup"><span data-stu-id="aea3b-277">In the second declaration, the contract type and metadata are implicit in the customized attribute.</span></span> <span data-ttu-id="aea3b-278">Especialmente em casos em que uma grande quantidade de metadados idênticos devem ser aplicados a várias partes (por exemplo, informações autorais ou de copyright), usar um atributo personalizado pode economizar bastante tempo e duplicação.</span><span class="sxs-lookup"><span data-stu-id="aea3b-278">Particularly in cases where a large amount of identical metadata must be applied to many parts (for example, author or copyright information), using a custom attribute can save a lot of time and duplication.</span></span> <span data-ttu-id="aea3b-279">Além disso, é possível criar árvores de herança de atributos personalizados para permitir variações.</span><span class="sxs-lookup"><span data-stu-id="aea3b-279">Further, inheritance trees of custom attributes can be created to allow for variations.</span></span>  
  
 <span data-ttu-id="aea3b-280">Para criar metadados opcionais em um atributo personalizado, você pode usar o atributo `DefaultValue`.</span><span class="sxs-lookup"><span data-stu-id="aea3b-280">To create optional metadata in a custom attribute, you can use the `DefaultValue` attribute.</span></span> <span data-ttu-id="aea3b-281">Quando esse atributo é aplicado a uma propriedade em uma classe de atributos personalizados, ele especifica que a propriedade decorada é opcional e não precisa ser fornecida por um exportador.</span><span class="sxs-lookup"><span data-stu-id="aea3b-281">When this attribute is applied to a property in a custom attribute class, it specifies that the decorated property is optional and does not have to be supplied by an exporter.</span></span> <span data-ttu-id="aea3b-282">Se um valor da propriedade não for fornecido, o valor padrão será designado a ela no tipo de propriedade (geralmente `null`, `false` ou 0.)</span><span class="sxs-lookup"><span data-stu-id="aea3b-282">If a value for the property is not supplied, it will be assigned the default value for its property type (usually `null`, `false`, or 0.)</span></span>  
  
<a name="creation_policies"></a>   
## <a name="creation-policies"></a><span data-ttu-id="aea3b-283">Políticas de criação</span><span class="sxs-lookup"><span data-stu-id="aea3b-283">Creation Policies</span></span>  
 <span data-ttu-id="aea3b-284">Quando uma parte especifica uma importação e a composição é realizada, o contêiner da composição tenta encontrar uma exportação correspondente.</span><span class="sxs-lookup"><span data-stu-id="aea3b-284">When a part specifies an import and composition is performed, the composition container attempts to find a matching export.</span></span> <span data-ttu-id="aea3b-285">Se a importação for correspondida a uma exportação com êxito, o membro da importação é definido como uma instância do objeto exportado.</span><span class="sxs-lookup"><span data-stu-id="aea3b-285">If it matches the import with an export successfully, the importing member is set to an instance of the exported object.</span></span> <span data-ttu-id="aea3b-286">O lugar de origem dessa instância é controlado pela *política de criação* da parte exportadora.</span><span class="sxs-lookup"><span data-stu-id="aea3b-286">Where this instance comes from is controlled by the exporting part's *creation policy*.</span></span>  
  
 <span data-ttu-id="aea3b-287">As duas políticas de criação possíveis são *compartilhada* e *não compartilhada*.</span><span class="sxs-lookup"><span data-stu-id="aea3b-287">The two possible creation policies are *shared* and *non-shared*.</span></span> <span data-ttu-id="aea3b-288">Uma parte com uma política de criação compartilhada será compartilhada entre cada importação no contêiner para uma parte com esse contrato.</span><span class="sxs-lookup"><span data-stu-id="aea3b-288">A part with a creation policy of shared will be shared between every import in the container for a part with that contract.</span></span> <span data-ttu-id="aea3b-289">Quando o mecanismo de composição encontra uma correspondência e precisa definir uma propriedade de importação, ele instanciará uma nova cópia da parte somente se ainda não existir uma; caso contrário, a cópia existente será fornecida.</span><span class="sxs-lookup"><span data-stu-id="aea3b-289">When the composition engine finds a match and has to set an importing property, it will instantiate a new copy of the part only if one does not already exist; otherwise, it will supply the existing copy.</span></span> <span data-ttu-id="aea3b-290">Isso significa que vários objetos possuem referências para a mesma parte.</span><span class="sxs-lookup"><span data-stu-id="aea3b-290">This means that many objects may have references to the same part.</span></span> <span data-ttu-id="aea3b-291">Essas partes não devem depender do estado interno que pode ser alterado a partir de diversos locais.</span><span class="sxs-lookup"><span data-stu-id="aea3b-291">Such parts should not rely on internal state that might be changed from many places.</span></span> <span data-ttu-id="aea3b-292">Essa política é adequada para partes estáticas, partes que oferecem serviços e partes que consomem muita memória ou outros recursos.</span><span class="sxs-lookup"><span data-stu-id="aea3b-292">This policy is appropriate for static parts, parts that provide services, and parts that consume a lot of memory or other resources.</span></span>  
  
 <span data-ttu-id="aea3b-293">Uma parte com a política de criação não compartilhada será criada toda vez que uma importação correspondente para uma das exportações for encontrada.</span><span class="sxs-lookup"><span data-stu-id="aea3b-293">A part with the creation policy of non-shared will be created every time a matching import for one of its exports is found.</span></span> <span data-ttu-id="aea3b-294">Uma nova cópia será, portanto, instanciada para cada importação no contêiner que corresponder a um dos contratos exportados da parte.</span><span class="sxs-lookup"><span data-stu-id="aea3b-294">A new copy will therefore be instantiated for every import in the container that matches one of the part's exported contracts.</span></span> <span data-ttu-id="aea3b-295">O estado interno dessas cópias não será compartilhado.</span><span class="sxs-lookup"><span data-stu-id="aea3b-295">The internal state of these copies will not be shared.</span></span> <span data-ttu-id="aea3b-296">Essa política é adequada para partes em que cada importação exigir seu próprio estado interno.</span><span class="sxs-lookup"><span data-stu-id="aea3b-296">This policy is appropriate for parts where each import requires its own internal state.</span></span>  
  
 <span data-ttu-id="aea3b-297">A importação e a exportação podem especificar a política de criação de uma parte, dentre os valores `Shared`, `NonShared` ou `Any`.</span><span class="sxs-lookup"><span data-stu-id="aea3b-297">Both the import and the export can specify the creation policy of a part, from among the values `Shared`, `NonShared`, or `Any`.</span></span> <span data-ttu-id="aea3b-298">O padrão é `Any` para importações e exportações.</span><span class="sxs-lookup"><span data-stu-id="aea3b-298">The default is `Any` for both imports and exports.</span></span> <span data-ttu-id="aea3b-299">Uma exportação que especifica `Shared` ou `NonShared` será correspondente somente a uma importação com a mesma especificação, ou que especificar `Any`.</span><span class="sxs-lookup"><span data-stu-id="aea3b-299">An export that specifies `Shared` or `NonShared` will only match an import that specifies the same, or that specifies `Any`.</span></span> <span data-ttu-id="aea3b-300">Da mesma forma, uma importação que especifica `Shared` ou `NonShared` será correspondente somente a uma exportação com a mesma especificação, ou que especificar `Any`.</span><span class="sxs-lookup"><span data-stu-id="aea3b-300">Similarly, an import that specifies `Shared` or `NonShared` will only match an export that specifies the same, or that specifies `Any`.</span></span> <span data-ttu-id="aea3b-301">Importações e exportações com políticas de criação incompatíveis não são consideradas correspondentes, da mesma maneira que uma importação e uma exportação cujo nome ou tipo de contrato não são correspondentes.</span><span class="sxs-lookup"><span data-stu-id="aea3b-301">Imports and exports with incompatible creation policies are not considered a match, in the same way as an import and export whose contract name or contract type are not a match.</span></span> <span data-ttu-id="aea3b-302">Se a importação e a exportação especificarem `Any`, ou não especificarem uma política de criação e o padrão for definido como `Any`, a política de criação será definida como compartilhada por padrão.</span><span class="sxs-lookup"><span data-stu-id="aea3b-302">If both import and export specify `Any`, or do not specify a creation policy and default to `Any`, the creation policy will default to shared.</span></span>  
  
 <span data-ttu-id="aea3b-303">O exemplo a seguir mostra importações e exportações que especificam políticas de criação.</span><span class="sxs-lookup"><span data-stu-id="aea3b-303">The following example shows both imports and exports specifying creation policies.</span></span> <span data-ttu-id="aea3b-304">`PartOne` não especifica uma política de criação, portanto, o padrão é `Any`.</span><span class="sxs-lookup"><span data-stu-id="aea3b-304">`PartOne` does not specify a creation policy, so the default is `Any`.</span></span> <span data-ttu-id="aea3b-305">`PartTwo` não especifica uma política de criação, portanto, o padrão é `Any`.</span><span class="sxs-lookup"><span data-stu-id="aea3b-305">`PartTwo` does not specify a creation policy, so the default is `Any`.</span></span> <span data-ttu-id="aea3b-306">Como o padrão da importação e da exportação é `Any`, `PartOne` será compartilhada.</span><span class="sxs-lookup"><span data-stu-id="aea3b-306">Since both import and export default to `Any`, `PartOne` will be shared.</span></span> <span data-ttu-id="aea3b-307">`PartThree` especifica uma política de criação `Shared`, portanto, `PartTwo` e `PartThree` compartilharão a mesma cópia de `PartOne`.</span><span class="sxs-lookup"><span data-stu-id="aea3b-307">`PartThree` specifies a `Shared` creation policy, so `PartTwo` and `PartThree` will share the same copy of `PartOne`.</span></span> <span data-ttu-id="aea3b-308">`PartFour` especifica uma política de criação `NonShared`, portanto, `PartFour` não será compartilhada em `PartFive`.</span><span class="sxs-lookup"><span data-stu-id="aea3b-308">`PartFour` specifies a `NonShared` creation policy, so `PartFour` will be non-shared in `PartFive`.</span></span> <span data-ttu-id="aea3b-309">`PartSix` especifica uma política de criação `NonShared`.</span><span class="sxs-lookup"><span data-stu-id="aea3b-309">`PartSix` specifies a `NonShared` creation policy.</span></span> <span data-ttu-id="aea3b-310">`PartFive` e `PartSix` receberão cópias separadas de `PartFour`.</span><span class="sxs-lookup"><span data-stu-id="aea3b-310">`PartFive` and `PartSix` will each receive separate copies of `PartFour`.</span></span> <span data-ttu-id="aea3b-311">`PartSeven` especifica uma política de criação `Shared`.</span><span class="sxs-lookup"><span data-stu-id="aea3b-311">`PartSeven` specifies a `Shared` creation policy.</span></span> <span data-ttu-id="aea3b-312">Como não há `PartFour` exportado com uma política de criação de `Shared`, a importação `PartSeven` não é correspondente a nada e não será preenchida.</span><span class="sxs-lookup"><span data-stu-id="aea3b-312">Because there is no exported `PartFour` with a creation policy of `Shared`, the `PartSeven` import does not match anything and will not be filled.</span></span>  
  
```vb  
<Export()>  
Public Class PartOne  
    'The default creation policy for an export is Any.  
End Class  
  
Public Class PartTwo  
  
    <Import()>  
    Public Property partOne As PartOne  
  
    'The default creation policy for an import is Any.  
    'If both policies are Any, the part will be shared.  
  
End Class  
  
Public Class PartThree  
  
    <Import(RequiredCreationPolicy:=CreationPolicy.Shared)>  
    Public Property partOne As PartOne  
  
    'The Shared creation policy is explicitly specified.  
    'PartTwo and PartThree will receive references to the  
    'SAME copy of PartOne.  
  
End Class  
  
<Export()>  
<PartCreationPolicy(CreationPolicy.NonShared)>  
Public Class PartFour  
    'The NonShared creation policy is explicitly specified.  
End Class  
  
Public Class PartFive  
  
    <Import()>  
    Public Property partFour As PartFour  
  
    'The default creation policy for an import is Any.  
    'Since the export's creation policy was explictly  
    'defined, the creation policy for this property will  
    'be non-shared.  
  
End Class  
  
Public Class PartSix  
  
    <Import(RequiredCreationPolicy:=CreationPolicy.NonShared)>  
    Public Property partFour As PartFour  
  
    'Both import and export specify matching creation   
    'policies.  PartFive and PartSix will each receive   
    'SEPARATE copies of PartFour, each with its own  
    'internal state.  
  
End Class  
  
Public Class PartSeven  
  
    <Import(RequiredCreationPolicy:=CreationPolicy.Shared)>  
    Public Property partFour As PartFour  
  
    'A creation policy mismatch.  Because there is no   
    'exported PartFour with a creation policy of Shared,  
    'this import does not match anything and will not be  
    'filled.  
  
End Class  
```  
  
```csharp  
[Export]  
public class PartOne  
{  
    //The default creation policy for an export is Any.  
}  
  
public class PartTwo  
{  
    [Import]  
    public PartOne partOne { get; set; }  
  
    //The default creation policy for an import is Any.  
    //If both policies are Any, the part will be shared.  
}  
  
public class PartThree  
{  
    [Import(RequiredCreationPolicy = CreationPolicy.Shared)]  
    public PartOne partOne { get; set; }  
  
    //The Shared creation policy is explicitly specified.  
    //PartTwo and PartThree will receive references to the  
    //SAME copy of PartOne.  
}  
  
[Export]  
[PartCreationPolicy(CreationPolicy.NonShared)]  
public class PartFour  
{  
    //The NonShared creation policy is explicitly specified.  
}  
  
public class PartFive  
{  
    [Import]  
    public PartFour partFour { get; set; }  
  
    //The default creation policy for an import is Any.  
    //Since the export's creation policy was explictly  
    //defined, the creation policy for this property will  
    //be non-shared.  
}  
  
public class PartSix  
{  
    [Import(RequiredCreationPolicy = CreationPolicy.NonShared)]  
    public PartFour partFour { get; set; }  
  
    //Both import and export specify matching creation   
    //policies.  PartFive and PartSix will each receive   
    //SEPARATE copies of PartFour, each with its own  
    //internal state.  
}  
  
public class PartSeven  
{  
    [Import(RequiredCreationPolicy = CreationPolicy.Shared)]  
    public PartFour partFour { get; set; }  
  
    //A creation policy mismatch.  Because there is no   
    //exported PartFour with a creation policy of Shared,  
    //this import does not match anything and will not be  
    //filled.  
}  
```  
  
<a name="life_cycle_and_disposing"></a>   
## <a name="life-cycle-and-disposing"></a><span data-ttu-id="aea3b-313">Ciclo de vida e descarte</span><span class="sxs-lookup"><span data-stu-id="aea3b-313">Life Cycle and Disposing</span></span>  
 <span data-ttu-id="aea3b-314">Uma vez que as partes estão hospedadas no contêiner de composição, seu ciclo de vida pode ser mais complexo do que objetos comuns.</span><span class="sxs-lookup"><span data-stu-id="aea3b-314">Because parts are hosted in the composition container, their life cycle can be more complex than ordinary objects.</span></span> <span data-ttu-id="aea3b-315">As partes podem implementar duas interfaces importantes relacionadas ao ciclo de vida: `IDisposable` e `IPartImportsSatisfiedNotification`.</span><span class="sxs-lookup"><span data-stu-id="aea3b-315">Parts can implement two important life cycle-related interfaces: `IDisposable` and `IPartImportsSatisfiedNotification`.</span></span>  
  
 <span data-ttu-id="aea3b-316">Partes que precisam que um trabalho seja realizado no desligamento ou que precisam ter recursos liberados devem implementar `IDisposable`, como é comum para objetos do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="aea3b-316">Parts that require work to be performed at shut down or that need to release resources should implement `IDisposable`, as usual for .NET Framework objects.</span></span> <span data-ttu-id="aea3b-317">No entanto, uma vez que o contêiner cria e mantém referências a partes, somente o contêiner que possui uma parte deve chamar o método `Dispose` em si.</span><span class="sxs-lookup"><span data-stu-id="aea3b-317">However, since the container creates and maintains references to parts, only the container that owns a part should call the `Dispose` method on it.</span></span> <span data-ttu-id="aea3b-318">O contêiner em si implementa `IDisposable` e, como parte de sua limpeza em `Dispose`, ele chamará `Dispose` em todas as partes que possui.</span><span class="sxs-lookup"><span data-stu-id="aea3b-318">The container itself implements `IDisposable`, and as portion of its cleanup in `Dispose` it will call `Dispose` on all the parts that it owns.</span></span> <span data-ttu-id="aea3b-319">Por esse motivo, você deve sempre descartar o contêiner de composição quando ele, e qualquer uma de suas partes, não for mais necessário.</span><span class="sxs-lookup"><span data-stu-id="aea3b-319">For this reason, you should always dispose the composition container when it and any parts it owns are no longer needed.</span></span>  
  
 <span data-ttu-id="aea3b-320">Para contêineres de composição de longa vida, o consumo de memória pelas partes com uma política de criação não compartilhada pode se tornar um problema.</span><span class="sxs-lookup"><span data-stu-id="aea3b-320">For long-lived composition containers, memory consumption by parts with a creation policy of non-shared can become a problem.</span></span> <span data-ttu-id="aea3b-321">Essas partes não compartilhadas podem ser criadas diversas vezes e não serão descartadas até que o contêiner em si seja descartado.</span><span class="sxs-lookup"><span data-stu-id="aea3b-321">These non-shared parts can be created multiple times and will not be disposed until the container itself is disposed.</span></span> <span data-ttu-id="aea3b-322">Para lidar com isso, o contêiner oferece o método `ReleaseExport`.</span><span class="sxs-lookup"><span data-stu-id="aea3b-322">To deal with this, the container provides the `ReleaseExport` method.</span></span> <span data-ttu-id="aea3b-323">Chamar esse método em uma exportação não compartilhada remove essa exportação do contêiner de composição e o descarta.</span><span class="sxs-lookup"><span data-stu-id="aea3b-323">Calling this method on a non-shared export removes that export from the composition container and disposes it.</span></span> <span data-ttu-id="aea3b-324">Partes que são usadas somente pela exportação removida, e assim por diante na árvore, também são removidas e descartadas.</span><span class="sxs-lookup"><span data-stu-id="aea3b-324">Parts that are used only by the removed export, and so on down the tree, are also removed and disposed.</span></span> <span data-ttu-id="aea3b-325">Dessa maneira, os recursos podem ser reivindicados novamente sem descartar o contêiner de composição em si.</span><span class="sxs-lookup"><span data-stu-id="aea3b-325">In this way, resources can be reclaimed without disposing the composition container itself.</span></span>  
  
 <span data-ttu-id="aea3b-326">`IPartImportsSatisfiedNotification` contém um método chamado `OnImportsSatisfied`.</span><span class="sxs-lookup"><span data-stu-id="aea3b-326">`IPartImportsSatisfiedNotification` contains one method named `OnImportsSatisfied`.</span></span> <span data-ttu-id="aea3b-327">Esse método é chamado pelo contêiner de composição em qualquer parte que implementar a interface quando a composição tiver sido concluída e as importações da parte estiverem prontas para uso.</span><span class="sxs-lookup"><span data-stu-id="aea3b-327">This method is called by the composition container on any parts that implement the interface when composition has been completed and the part's imports are ready for use.</span></span> <span data-ttu-id="aea3b-328">As partes são criadas pelo mecanismo de composição para preencher as importações de outras partes.</span><span class="sxs-lookup"><span data-stu-id="aea3b-328">Parts are created by the composition engine to fill the imports of other parts.</span></span> <span data-ttu-id="aea3b-329">Antes de as importações de uma parte terem sido definidas, você não pode realizar nenhuma inicialização que dependa de ou manipule valores importados no construtor da parte, a menos que esses valores tenham sido especificados como pré-requisitos usando o atributo `ImportingConstructor`.</span><span class="sxs-lookup"><span data-stu-id="aea3b-329">Before the imports of a part have been set, you cannot perform any initialization that relies on or manipulates imported values in the part constructor unless those values have been specified as prerequisites by using the `ImportingConstructor` attribute.</span></span> <span data-ttu-id="aea3b-330">Normalmente, esse é o método preferido, mas, em alguns casos, a injeção do construtor pode não estar disponível.</span><span class="sxs-lookup"><span data-stu-id="aea3b-330">This is normally the preferred method, but in some cases, constructor injection may not be available.</span></span> <span data-ttu-id="aea3b-331">Na maioria dos casos, a inicialização pode ser realizada em `OnImportsSatisfied`, e a parte deve implementar `IPartImportsSatisfiedNotification`.</span><span class="sxs-lookup"><span data-stu-id="aea3b-331">In those cases, initialization can be performed in `OnImportsSatisfied`, and the part should implement `IPartImportsSatisfiedNotification`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aea3b-332">Consulte também</span><span class="sxs-lookup"><span data-stu-id="aea3b-332">See Also</span></span>  
 [<span data-ttu-id="aea3b-333">Vídeo do Channel 9: Open Up Your Applications with the Managed Extensibility Framework (Abra seus aplicativos com o Managed Extensibility Framework)</span><span class="sxs-lookup"><span data-stu-id="aea3b-333">Channel 9 Video: Open Up Your Applications with the Managed Extensibility Framework</span></span>](https://channel9.msdn.com/events/TechEd/NorthAmerica/2009/DTL328)  
 <span data-ttu-id="aea3b-334">[Vídeo do Channel 9: Managed Extensibility Framework (MEF) 2.0 [MEF (Managed Extensibility Framework) 2.0]](https://channel9.msdn.com/posts/NET-45-Oleg-Lvovitch-and-Kevin-Ransom-Managed-Extensibility-Framework-MEF-20)</span><span class="sxs-lookup"><span data-stu-id="aea3b-334">[Channel 9 Video: Managed Extensibility Framework (MEF) 2.0](https://channel9.msdn.com/posts/NET-45-Oleg-Lvovitch-and-Kevin-Ransom-Managed-Extensibility-Framework-MEF-20)</span></span>
