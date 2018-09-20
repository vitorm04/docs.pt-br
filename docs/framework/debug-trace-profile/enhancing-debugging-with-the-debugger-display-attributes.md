---
title: Melhorando a depuração com os atributos de exibição do depurador
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- debugger, display attributes
- DebuggerTypeProxyAttribute attribute
- debugging [.NET Framework], debugger display attributes
- DebuggerDisplayAttribute attribute
- display attributes for debugger
- DebuggerBrowsableAttribute attribute
ms.assetid: 72bb7aa9-459b-42c4-9163-9312fab4c410
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 880504e874d9797cf05290058b6dbf3a3daf2579
ms.sourcegitcommit: 3ab9254890a52a50762995fa6d7d77a00348db7e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/20/2018
ms.locfileid: "46473110"
---
# <a name="enhancing-debugging-with-the-debugger-display-attributes"></a><span data-ttu-id="9d1c9-102">Melhorando a depuração com os atributos de exibição do depurador</span><span class="sxs-lookup"><span data-stu-id="9d1c9-102">Enhancing Debugging with the Debugger Display Attributes</span></span>
<span data-ttu-id="9d1c9-103">Os atributos de exibição do depurador permitem ao desenvolvedor do tipo, que especifica e entende melhor o comportamento de tempo de execução desse tipo, especificar também a aparência desse tipo quando ele é exibido em um depurador.</span><span class="sxs-lookup"><span data-stu-id="9d1c9-103">Debugger display attributes allow the developer of the type, who specifies and best understands the runtime behavior of that type, to also specify what that type will look like when it is displayed in a debugger.</span></span> <span data-ttu-id="9d1c9-104">Além disso, os atributos de exibição do depurador que fornecem uma propriedade `Target` podem ser aplicados no nível do assembly pelos usuários sem conhecimento do código-fonte.</span><span class="sxs-lookup"><span data-stu-id="9d1c9-104">In addition, debugger display attributes that provide a `Target` property can be applied at the assembly level by users without knowledge of the source code.</span></span> <span data-ttu-id="9d1c9-105">O atributo <xref:System.Diagnostics.DebuggerDisplayAttribute> controla como um tipo ou um membro é exibido nas janelas de variáveis do depurador.</span><span class="sxs-lookup"><span data-stu-id="9d1c9-105">The <xref:System.Diagnostics.DebuggerDisplayAttribute> attribute controls how a type or member is displayed in the debugger variable windows.</span></span> <span data-ttu-id="9d1c9-106">O atributo <xref:System.Diagnostics.DebuggerBrowsableAttribute> determina se e como um campo ou uma propriedade é exibida nas janelas de variáveis do depurador.</span><span class="sxs-lookup"><span data-stu-id="9d1c9-106">The <xref:System.Diagnostics.DebuggerBrowsableAttribute> attribute determines if and how a field or property is displayed in the debugger variable windows.</span></span> <span data-ttu-id="9d1c9-107">O atributo <xref:System.Diagnostics.DebuggerTypeProxyAttribute> especifica um tipo substituto ou um proxy, para um tipo e altera o modo como o tipo é exibido nas janelas do depurador.</span><span class="sxs-lookup"><span data-stu-id="9d1c9-107">The <xref:System.Diagnostics.DebuggerTypeProxyAttribute> attribute specifies a substitute type, or a proxy, for a type and changes the way the type is displayed in debugger windows.</span></span> <span data-ttu-id="9d1c9-108">Quando você exibe uma variável que tem um proxy ou um tipo substituto, o proxy substitui o tipo original na janela de exibição do depurador.</span><span class="sxs-lookup"><span data-stu-id="9d1c9-108">When you view a variable that has a proxy, or substitute type, the proxy stands in for the original type in the debugger display window.</span></span> <span data-ttu-id="9d1c9-109">A janela de variáveis do depurador exibe apenas os membros públicos do tipo de proxy.</span><span class="sxs-lookup"><span data-stu-id="9d1c9-109">The debugger variable window displays only the public members of the proxy type.</span></span> <span data-ttu-id="9d1c9-110">Os membros particulares não são exibidos.</span><span class="sxs-lookup"><span data-stu-id="9d1c9-110">Private members are not displayed.</span></span>  
  
## <a name="using-the-debuggerdisplayattribute"></a><span data-ttu-id="9d1c9-111">Usando o DebuggerDisplayAttribute</span><span class="sxs-lookup"><span data-stu-id="9d1c9-111">Using the DebuggerDisplayAttribute</span></span>  
 <span data-ttu-id="9d1c9-112">O construtor <xref:System.Diagnostics.DebuggerDisplayAttribute.%23ctor%2A> tem um único argumento: uma cadeia de caracteres a ser exibida na coluna de valor das instâncias do tipo.</span><span class="sxs-lookup"><span data-stu-id="9d1c9-112">The <xref:System.Diagnostics.DebuggerDisplayAttribute.%23ctor%2A> constructor has a single argument: a string to be displayed in the value column for instances of the type.</span></span> <span data-ttu-id="9d1c9-113">Essa cadeia de caracteres pode conter chaves ({ e }).</span><span class="sxs-lookup"><span data-stu-id="9d1c9-113">This string can contain braces ({ and }).</span></span> <span data-ttu-id="9d1c9-114">O texto dentro de um par de chaves é avaliado como uma expressão.</span><span class="sxs-lookup"><span data-stu-id="9d1c9-114">The text within a pair of braces is evaluated as an expression.</span></span> <span data-ttu-id="9d1c9-115">Por exemplo, o código C# a seguir faz com que “Contagem = 4” seja exibida quando o sinal de adição (+) é selecionado para expandir a exibição do depurador para uma instância de `MyHashtable`.</span><span class="sxs-lookup"><span data-stu-id="9d1c9-115">For example, the following C# code causes "Count = 4" to be displayed when the plus sign (+) is selected to expand the debugger display for an instance of `MyHashtable`.</span></span>  
  
```csharp
[DebuggerDisplay("Count = {count}")]  
class MyHashtable  
{  
    public int count = 4;  
}  
```
  
 <span data-ttu-id="9d1c9-116">Os atributos aplicados às propriedades referenciadas na expressão não são processados.</span><span class="sxs-lookup"><span data-stu-id="9d1c9-116">Attributes applied to properties referenced in the expression are not processed.</span></span> <span data-ttu-id="9d1c9-117">Para o compilador C#, uma expressão geral é permitida que tem somente acesso implícito a essa referência na instância atual do tipo de destino.</span><span class="sxs-lookup"><span data-stu-id="9d1c9-117">For the C# compiler, a general expression is allowed that has only implicit access to this reference for the current instance of the target type.</span></span> <span data-ttu-id="9d1c9-118">A expressão é limitada; não há nenhum acesso a aliases, locais ou ponteiros.</span><span class="sxs-lookup"><span data-stu-id="9d1c9-118">The expression is limited; there is no access to aliases, locals, or pointers.</span></span> <span data-ttu-id="9d1c9-119">No código C#, você pode usar uma expressão geral entre as chaves que tem acesso implícito ao ponteiro `this` na instância atual somente do tipo de destino.</span><span class="sxs-lookup"><span data-stu-id="9d1c9-119">In C# code, you can use a general expression between the braces that has implicit access to the `this` pointer for the current instance of the target type only.</span></span>  
  
 <span data-ttu-id="9d1c9-120">Por exemplo, se um objeto do C# tiver um `ToString()` substituído, o depurador chamará a substituição e mostrará seu resultado, em vez do `{<typeName>}.` padrão. Portanto, se você tiver substituído `ToString()`, não precisará usar <xref:System.Diagnostics.DebuggerDisplayAttribute>.</span><span class="sxs-lookup"><span data-stu-id="9d1c9-120">For example, if a C# object has an overridden `ToString()`, the debugger will call the override and show its result instead of the standard `{<typeName>}.` Thus, if you have overridden `ToString()`, you do not need to use <xref:System.Diagnostics.DebuggerDisplayAttribute>.</span></span> <span data-ttu-id="9d1c9-121">Se você usar ambas, o atributo <xref:System.Diagnostics.DebuggerDisplayAttribute> terá precedência sobre a substituição de `ToString()`.</span><span class="sxs-lookup"><span data-stu-id="9d1c9-121">If you use both, the <xref:System.Diagnostics.DebuggerDisplayAttribute> attribute takes precedence over the `ToString()` override.</span></span>  
  
## <a name="using-the-debuggerbrowsableattribute"></a><span data-ttu-id="9d1c9-122">Usando o DebuggerBrowsableAttribute</span><span class="sxs-lookup"><span data-stu-id="9d1c9-122">Using the DebuggerBrowsableAttribute</span></span>  
 <span data-ttu-id="9d1c9-123">Aplique o <xref:System.Diagnostics.DebuggerBrowsableAttribute> a um campo ou uma propriedade para especificar como o campo ou a propriedade deve ser exibida na janela do depurador.</span><span class="sxs-lookup"><span data-stu-id="9d1c9-123">Apply the <xref:System.Diagnostics.DebuggerBrowsableAttribute> to a field or property to specify how the field or property is to be displayed in the debugger window.</span></span> <span data-ttu-id="9d1c9-124">O construtor desse atributo usa um dos valores de enumeração <xref:System.Diagnostics.DebuggerBrowsableState>, que especifica um dos seguintes estados:</span><span class="sxs-lookup"><span data-stu-id="9d1c9-124">The constructor for this attribute takes one of the <xref:System.Diagnostics.DebuggerBrowsableState> enumeration values, which specifies one of the following states:</span></span>  
  
-   <span data-ttu-id="9d1c9-125"><xref:System.Diagnostics.DebuggerBrowsableState.Never> indica que o membro não é exibido na janela de dados.</span><span class="sxs-lookup"><span data-stu-id="9d1c9-125"><xref:System.Diagnostics.DebuggerBrowsableState.Never> indicates that the member is not displayed in the data window.</span></span>  <span data-ttu-id="9d1c9-126">Por exemplo, o uso desse valor para o <xref:System.Diagnostics.DebuggerBrowsableAttribute> em um campo remove o campo da hierarquia; o campo não é exibido quando você expande o tipo delimitador clicando no sinal de adição (+) da instância de tipo.</span><span class="sxs-lookup"><span data-stu-id="9d1c9-126">For example, using this value for the <xref:System.Diagnostics.DebuggerBrowsableAttribute> on a field removes the field from the hierarchy; the field is not displayed when you expand the enclosing type by clicking the plus sign (+) for the type instance.</span></span>  
  
-   <span data-ttu-id="9d1c9-127"><xref:System.Diagnostics.DebuggerBrowsableState.Collapsed> indica que o membro é exibido, mas não expandido por padrão.</span><span class="sxs-lookup"><span data-stu-id="9d1c9-127"><xref:System.Diagnostics.DebuggerBrowsableState.Collapsed> indicates that the member is displayed but not expanded by default.</span></span>  <span data-ttu-id="9d1c9-128">Este é o comportamento padrão.</span><span class="sxs-lookup"><span data-stu-id="9d1c9-128">This is the default behavior.</span></span>  
  
-   <span data-ttu-id="9d1c9-129"><xref:System.Diagnostics.DebuggerBrowsableState.RootHidden> indica que o próprio membro não é mostrado, mas seus objetos constituintes são exibidos, se ele é uma matriz ou uma coleção.</span><span class="sxs-lookup"><span data-stu-id="9d1c9-129"><xref:System.Diagnostics.DebuggerBrowsableState.RootHidden> indicates that the member itself is not shown, but its constituent objects are displayed if it is an array or collection.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9d1c9-130">Não há suporte para o <xref:System.Diagnostics.DebuggerBrowsableAttribute> no Visual Basic no .NET Framework versão 2.0.</span><span class="sxs-lookup"><span data-stu-id="9d1c9-130">The <xref:System.Diagnostics.DebuggerBrowsableAttribute> is not supported by Visual Basic in the .NET Framework version 2.0.</span></span>  
  
 <span data-ttu-id="9d1c9-131">O exemplo de código a seguir mostra o uso do <xref:System.Diagnostics.DebuggerBrowsableAttribute> para impedir que a propriedade após ele seja exibida na janela de depuração da classe.</span><span class="sxs-lookup"><span data-stu-id="9d1c9-131">The following code example shows the use of the <xref:System.Diagnostics.DebuggerBrowsableAttribute> to prevent the property following it from appearing in the debug window for the class.</span></span>  
  
```csharp
[DebuggerBrowsable(DebuggerBrowsableState.Never)]  
public static string y = "Test String";  
```  
  
## <a name="using-the-debuggertypeproxy"></a><span data-ttu-id="9d1c9-132">Usando o DebuggerTypeProxy</span><span class="sxs-lookup"><span data-stu-id="9d1c9-132">Using the DebuggerTypeProxy</span></span>  
 <span data-ttu-id="9d1c9-133">Use o atributo <xref:System.Diagnostics.DebuggerTypeProxyAttribute> quando você precisar alterar a exibição de depuração de um tipo de forma significativa e básica, mas não o próprio tipo.</span><span class="sxs-lookup"><span data-stu-id="9d1c9-133">Use the <xref:System.Diagnostics.DebuggerTypeProxyAttribute> attribute when you need to significantly and fundamentally change the debugging view of a type, but not change the type itself.</span></span> <span data-ttu-id="9d1c9-134">O atributo <xref:System.Diagnostics.DebuggerTypeProxyAttribute> é usado para especificar um proxy de exibição para um tipo, permitindo que um desenvolvedor adapte a exibição para o tipo.</span><span class="sxs-lookup"><span data-stu-id="9d1c9-134">The <xref:System.Diagnostics.DebuggerTypeProxyAttribute> attribute is used to specify a display proxy for a type, allowing a developer to tailor the view for the type.</span></span>  <span data-ttu-id="9d1c9-135">Este atributo, como o <xref:System.Diagnostics.DebuggerDisplayAttribute>, pode ser usado no nível do assembly, caso em que a propriedade <xref:System.Diagnostics.DebuggerTypeProxyAttribute.Target%2A> especifica o tipo para o qual o proxy será usado.</span><span class="sxs-lookup"><span data-stu-id="9d1c9-135">This attribute, like the <xref:System.Diagnostics.DebuggerDisplayAttribute>, can be used at the assembly level, in which case the <xref:System.Diagnostics.DebuggerTypeProxyAttribute.Target%2A> property specifies the type for which the proxy will be used.</span></span> <span data-ttu-id="9d1c9-136">O uso recomendado é que este atributo especifique um tipo aninhado particular que ocorre dentro do tipo ao qual o atributo é aplicado.</span><span class="sxs-lookup"><span data-stu-id="9d1c9-136">The recommended usage is that this attribute specifies a private nested type that occurs within the type to which the attribute is applied.</span></span>  <span data-ttu-id="9d1c9-137">Um avaliador de expressão que dá suporte a visualizadores de tipo verifica se esse atributo existe quando um tipo é exibido.</span><span class="sxs-lookup"><span data-stu-id="9d1c9-137">An expression evaluator that supports type viewers checks for this attribute when a type is displayed.</span></span> <span data-ttu-id="9d1c9-138">Se o atributo for encontrado, o avaliador de expressão substituirá o tipo de proxy de exibição do tipo ao qual o atributo é aplicado.</span><span class="sxs-lookup"><span data-stu-id="9d1c9-138">If the attribute is found, the expression evaluator substitutes the display proxy type for the type the attribute is applied to.</span></span>  
  
 <span data-ttu-id="9d1c9-139">Quando o <xref:System.Diagnostics.DebuggerTypeProxyAttribute> está presente, a janela de variáveis do depurador exibe apenas os membros públicos do tipo de proxy.</span><span class="sxs-lookup"><span data-stu-id="9d1c9-139">When the <xref:System.Diagnostics.DebuggerTypeProxyAttribute> is present, the debugger variable window displays only the public members of the proxy type.</span></span> <span data-ttu-id="9d1c9-140">Os membros particulares não são exibidos.</span><span class="sxs-lookup"><span data-stu-id="9d1c9-140">Private members are not displayed.</span></span> <span data-ttu-id="9d1c9-141">O comportamento da janela de dados não é alterado por exibições aprimoradas por atributo.</span><span class="sxs-lookup"><span data-stu-id="9d1c9-141">The behavior of the data window is not changed by attribute-enhanced views.</span></span>  
  
 <span data-ttu-id="9d1c9-142">Para evitar penalidades de desempenho desnecessárias, os atributos do proxy de exibição não são processados até que o objeto seja expandido, por meio do clique pelo usuário no sinal de adição (+) ao lado do tipo em uma janela de dados ou por meio da aplicação do atributo <xref:System.Diagnostics.DebuggerBrowsableAttribute>.</span><span class="sxs-lookup"><span data-stu-id="9d1c9-142">To avoid unnecessary performance penalties, attributes of the display proxy are not processed until the object is expanded, either through the user clicking the plus sign (+) next to the type in a data window, or through the application of the <xref:System.Diagnostics.DebuggerBrowsableAttribute> attribute.</span></span> <span data-ttu-id="9d1c9-143">Portanto, é recomendável que nenhum atributo seja aplicado ao tipo de exibição.</span><span class="sxs-lookup"><span data-stu-id="9d1c9-143">Therefore, it is recommended that no attributes be applied to the display type.</span></span> <span data-ttu-id="9d1c9-144">Os atributos podem e devem ser aplicados no corpo do tipo de exibição.</span><span class="sxs-lookup"><span data-stu-id="9d1c9-144">Attributes can and should be applied within the body of the display type.</span></span>  
  
 <span data-ttu-id="9d1c9-145">O exemplo de código a seguir mostra o uso do <xref:System.Diagnostics.DebuggerTypeProxyAttribute> para especificar um tipo a ser usado como um proxy de exibição do depurador.</span><span class="sxs-lookup"><span data-stu-id="9d1c9-145">The following code example shows the use of the <xref:System.Diagnostics.DebuggerTypeProxyAttribute> to specify a type to be used as a debugger display proxy.</span></span>  
  
```csharp
[DebuggerTypeProxy(typeof(HashtableDebugView))]  
class MyHashtable : Hashtable  
{  
    private const string TestString =   
        "This should not appear in the debug window.";  
  
    internal class HashtableDebugView  
    {  
        private Hashtable hashtable;  
        public const string TestStringProxy =   
            "This should appear in the debug window.";  
  
        // The constructor for the type proxy class must have a   
        // constructor that takes the target type as a parameter.  
        public HashtableDebugView(Hashtable hashtable)  
        {  
            this.hashtable = hashtable;  
        }  
    }  
}  
```  
  
## <a name="example"></a><span data-ttu-id="9d1c9-146">Exemplo</span><span class="sxs-lookup"><span data-stu-id="9d1c9-146">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="9d1c9-147">Descrição</span><span class="sxs-lookup"><span data-stu-id="9d1c9-147">Description</span></span>  
 <span data-ttu-id="9d1c9-148">O exemplo de código a seguir pode ser exibido no [!INCLUDE[vsprvslong](../../../includes/vsprvslong-md.md)] para ver os resultados da aplicação dos atributos <xref:System.Diagnostics.DebuggerDisplayAttribute>, <xref:System.Diagnostics.DebuggerBrowsableAttribute> e <xref:System.Diagnostics.DebuggerTypeProxyAttribute>.</span><span class="sxs-lookup"><span data-stu-id="9d1c9-148">The following code example can be viewed in [!INCLUDE[vsprvslong](../../../includes/vsprvslong-md.md)] to see the results of applying the <xref:System.Diagnostics.DebuggerDisplayAttribute>, <xref:System.Diagnostics.DebuggerBrowsableAttribute>, and <xref:System.Diagnostics.DebuggerTypeProxyAttribute> attributes.</span></span>  
  
### <a name="code"></a><span data-ttu-id="9d1c9-149">Código</span><span class="sxs-lookup"><span data-stu-id="9d1c9-149">Code</span></span>  
 [!code-cpp[System.Diagnostics.DebuggerBrowsableAttribute#1](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.Diagnostics.DebuggerBrowsableAttribute/cpp/program.cpp#1)]
 [!code-csharp[System.Diagnostics.DebuggerBrowsableAttribute#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.Diagnostics.DebuggerBrowsableAttribute/CS/program.cs#1)]
 [!code-vb[System.Diagnostics.DebuggerBrowsableAttribute#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.Diagnostics.DebuggerBrowsableAttribute/VB/module1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="9d1c9-150">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9d1c9-150">See Also</span></span>  
 <xref:System.Diagnostics.DebuggerDisplayAttribute>  
 <xref:System.Diagnostics.DebuggerBrowsableAttribute>  
 <xref:System.Diagnostics.DebuggerTypeProxyAttribute>
