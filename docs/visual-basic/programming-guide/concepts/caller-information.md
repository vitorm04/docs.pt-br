---
title: "Informações do chamador (Visual Basic) | Documentos do Microsoft"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
ms.assetid: 15d556eb-4d0c-4497-98a3-7f60abb7d6a1
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: d9a028474a3bb7ae020f466d4dfe51608c43ab07
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="caller-information-visual-basic"></a><span data-ttu-id="ab43c-102">Informações do chamador (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ab43c-102">Caller Information (Visual Basic)</span></span>
<span data-ttu-id="ab43c-103">Ao usar atributos de informações do chamador, você pode obter informações sobre o chamador de um método.</span><span class="sxs-lookup"><span data-stu-id="ab43c-103">By using Caller Info attributes, you can obtain information about the caller to a method.</span></span> <span data-ttu-id="ab43c-104">Você pode obter o caminho do arquivo do código-fonte, o número da linha no código-fonte e o nome do membro do chamador.</span><span class="sxs-lookup"><span data-stu-id="ab43c-104">You can obtain file path of the source code, the line number in the source code, and the member name of the caller.</span></span> <span data-ttu-id="ab43c-105">Essas informações são úteis para fins de rastreamento, depuração e criação de ferramentas de diagnóstico.</span><span class="sxs-lookup"><span data-stu-id="ab43c-105">This information is helpful for tracing, debugging, and creating diagnostic tools.</span></span>  
  
 <span data-ttu-id="ab43c-106">Para obter essas informações, você deve usar os atributos que são aplicadas aos parâmetros opcionais, cada qual com um valor padrão.</span><span class="sxs-lookup"><span data-stu-id="ab43c-106">To obtain this information, you use attributes that are applied to optional parameters, each of which has a default value.</span></span> <span data-ttu-id="ab43c-107">A tabela a seguir lista os atributos de informações do chamador que são definidos na <xref:System.Runtime.CompilerServices?displayProperty=fullName>namespace:</xref:System.Runtime.CompilerServices?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="ab43c-107">The following table lists the Caller Info attributes that are defined in the <xref:System.Runtime.CompilerServices?displayProperty=fullName> namespace:</span></span>  
  
|<span data-ttu-id="ab43c-108">Atributo</span><span class="sxs-lookup"><span data-stu-id="ab43c-108">Attribute</span></span>|<span data-ttu-id="ab43c-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="ab43c-109">Description</span></span>|<span data-ttu-id="ab43c-110">Tipo</span><span class="sxs-lookup"><span data-stu-id="ab43c-110">Type</span></span>|  
|---|---|---|  
|<span data-ttu-id="ab43c-111"><xref:System.Runtime.CompilerServices.CallerFilePathAttribute></xref:System.Runtime.CompilerServices.CallerFilePathAttribute></span><span class="sxs-lookup"><span data-stu-id="ab43c-111"><xref:System.Runtime.CompilerServices.CallerFilePathAttribute></span></span>|<span data-ttu-id="ab43c-112">O caminho completo do arquivo de origem que contém o chamador.</span><span class="sxs-lookup"><span data-stu-id="ab43c-112">Full path of the source file that contains the caller.</span></span> <span data-ttu-id="ab43c-113">Esse é o caminho do arquivo no momento da compilação.</span><span class="sxs-lookup"><span data-stu-id="ab43c-113">This is the file path at compile time.</span></span>|`String`|  
|<span data-ttu-id="ab43c-114"><xref:System.Runtime.CompilerServices.CallerLineNumberAttribute></xref:System.Runtime.CompilerServices.CallerLineNumberAttribute></span><span class="sxs-lookup"><span data-stu-id="ab43c-114"><xref:System.Runtime.CompilerServices.CallerLineNumberAttribute></span></span>|<span data-ttu-id="ab43c-115">Número da linha no arquivo fonte no qual o método é chamado.</span><span class="sxs-lookup"><span data-stu-id="ab43c-115">Line number in the source file at which the method is called.</span></span>|`Integer`|  
|<span data-ttu-id="ab43c-116"><xref:System.Runtime.CompilerServices.CallerMemberNameAttribute></xref:System.Runtime.CompilerServices.CallerMemberNameAttribute></span><span class="sxs-lookup"><span data-stu-id="ab43c-116"><xref:System.Runtime.CompilerServices.CallerMemberNameAttribute></span></span>|<span data-ttu-id="ab43c-117">Nome do método ou da propriedade do chamador.</span><span class="sxs-lookup"><span data-stu-id="ab43c-117">Method or property name of the caller.</span></span> <span data-ttu-id="ab43c-118">Consulte [nomes de membro](#MEMBERNAMES) mais adiante neste tópico.</span><span class="sxs-lookup"><span data-stu-id="ab43c-118">See [Member Names](#MEMBERNAMES) later in this topic.</span></span>|`String`|  
  
## <a name="example"></a><span data-ttu-id="ab43c-119">Exemplo</span><span class="sxs-lookup"><span data-stu-id="ab43c-119">Example</span></span>  
 <span data-ttu-id="ab43c-120">O exemplo a seguir mostra como usar os atributos de informações do chamador.</span><span class="sxs-lookup"><span data-stu-id="ab43c-120">The following example shows how to use Caller Info attributes.</span></span> <span data-ttu-id="ab43c-121">Em cada chamada para o método `TraceMessage`, as informações do chamador são substituídas como argumentos para os parâmetros opcionais.</span><span class="sxs-lookup"><span data-stu-id="ab43c-121">On each call to the `TraceMessage` method, the caller information is substituted as arguments to the optional parameters.</span></span>  
  
```vb  
Private Sub DoProcessing()  
    TraceMessage("Something happened.")  
End Sub  
  
Public Sub TraceMessage(message As String,  
        <System.Runtime.CompilerServices.CallerMemberName> Optional memberName As String = Nothing,  
        <System.Runtime.CompilerServices.CallerFilePath> Optional sourcefilePath As String = Nothing,  
        <System.Runtime.CompilerServices.CallerLineNumber()> Optional sourceLineNumber As Integer = 0)  
  
    System.Diagnostics.Trace.WriteLine("message: " & message)  
    System.Diagnostics.Trace.WriteLine("member name: " & memberName)  
    System.Diagnostics.Trace.WriteLine("source file path: " & sourcefilePath)  
    System.Diagnostics.Trace.WriteLine("source line number: " & sourceLineNumber)  
End Sub  
  
' Sample output:  
'   message: Something happened.  
'   member name: DoProcessing  
'   source file path: C:\Users\username\Documents\Visual Studio 2012\Projects\CallerInfoVB\CallerInfoVB\Form1.vb  
'   source line number: 15  
```  
  
## <a name="remarks"></a><span data-ttu-id="ab43c-122">Comentários</span><span class="sxs-lookup"><span data-stu-id="ab43c-122">Remarks</span></span>  
 <span data-ttu-id="ab43c-123">Você deve especificar um valor padrão explícito para cada parâmetro opcional.</span><span class="sxs-lookup"><span data-stu-id="ab43c-123">You must specify an explicit default value for each optional parameter.</span></span> <span data-ttu-id="ab43c-124">Você não pode aplicar atributos de informações do chamador aos parâmetros que não são especificados como opcionais.</span><span class="sxs-lookup"><span data-stu-id="ab43c-124">You can't apply Caller Info attributes to parameters that aren't specified as optional.</span></span>  
  
 <span data-ttu-id="ab43c-125">Os atributos de informações do chamador não tornam um parâmetro opcional.</span><span class="sxs-lookup"><span data-stu-id="ab43c-125">The Caller Info attributes don't make a parameter optional.</span></span> <span data-ttu-id="ab43c-126">Em vez disso, eles afetam o valor padrão que é passado quando o argumento é omitido.</span><span class="sxs-lookup"><span data-stu-id="ab43c-126">Instead, they affect the default value that's passed in when the argument is omitted.</span></span>  
  
 <span data-ttu-id="ab43c-127">Os valores de informações do chamador são emitidos como literais em linguagem intermediária (IL) em tempo de compilação.</span><span class="sxs-lookup"><span data-stu-id="ab43c-127">Caller Info values are emitted as literals into the Intermediate Language (IL) at compile time.</span></span> <span data-ttu-id="ab43c-128">Ao contrário dos resultados do <xref:System.Exception.StackTrace%2A>propriedade para exceções, os resultados não são afetados por ofuscamento.</xref:System.Exception.StackTrace%2A></span><span class="sxs-lookup"><span data-stu-id="ab43c-128">Unlike the results of the <xref:System.Exception.StackTrace%2A> property for exceptions, the results aren't affected by obfuscation.</span></span>  
  
 <span data-ttu-id="ab43c-129">Você pode fornecer explicitamente os argumentos opcionais para controlar as informações do chamador ou ocultá-las.</span><span class="sxs-lookup"><span data-stu-id="ab43c-129">You can explicitly supply the optional arguments to control the caller information or to hide caller information.</span></span>  
  
###  <span data-ttu-id="ab43c-130"><a name="MEMBERNAMES"></a>Nomes de membro</span><span class="sxs-lookup"><span data-stu-id="ab43c-130"><a name="MEMBERNAMES"></a> Member Names</span></span>  
 <span data-ttu-id="ab43c-131">Você pode usar o atributo `CallerMemberName` para evitar especificar o nome do membro como um argumento `String` ao método chamado.</span><span class="sxs-lookup"><span data-stu-id="ab43c-131">You can use the `CallerMemberName` attribute to avoid specifying the member name as a `String` argument to the called method.</span></span> <span data-ttu-id="ab43c-132">Usando essa técnica, você pode evitar o problema que **refatoração Renomear** não altera o `String` valores.</span><span class="sxs-lookup"><span data-stu-id="ab43c-132">By using this technique, you avoid the problem that **Rename Refactoring** doesn't change the `String` values.</span></span> <span data-ttu-id="ab43c-133">Esse benefício é especialmente útil para as seguintes tarefas:</span><span class="sxs-lookup"><span data-stu-id="ab43c-133">This benefit is especially useful for the following tasks:</span></span>  
  
-   <span data-ttu-id="ab43c-134">Usar rotinas de rastreamento e diagnóstico.</span><span class="sxs-lookup"><span data-stu-id="ab43c-134">Using tracing and diagnostic routines.</span></span>  
  
-   <span data-ttu-id="ab43c-135">Implementando o <xref:System.ComponentModel.INotifyPropertyChanged>ao associar dados da interface.</xref:System.ComponentModel.INotifyPropertyChanged></span><span class="sxs-lookup"><span data-stu-id="ab43c-135">Implementing the <xref:System.ComponentModel.INotifyPropertyChanged> interface when binding data.</span></span> <span data-ttu-id="ab43c-136">Essa interface permite que a propriedade de um objeto notifique um controle associado sobre a alteração da propriedade de modo que o controle possa exibir as informações atualizadas.</span><span class="sxs-lookup"><span data-stu-id="ab43c-136">This interface allows the property of an object to notify a bound control that the property has changed, so that the control can display the updated information.</span></span> <span data-ttu-id="ab43c-137">Sem o atributo `CallerMemberName`, você deve especificar o nome da propriedade como um literal.</span><span class="sxs-lookup"><span data-stu-id="ab43c-137">Without the `CallerMemberName` attribute, you must specify the property name as a literal.</span></span>  
  
 <span data-ttu-id="ab43c-138">O gráfico a seguir mostra os nomes de membros que são retornados quando você usa o atributo `CallerMemberName`.</span><span class="sxs-lookup"><span data-stu-id="ab43c-138">The following chart shows the member names that are returned when you use the `CallerMemberName` attribute.</span></span>  
  
|<span data-ttu-id="ab43c-139">As chamadas ocorrem em</span><span class="sxs-lookup"><span data-stu-id="ab43c-139">Calls occurs within</span></span>|<span data-ttu-id="ab43c-140">Resultado de nome de membro</span><span class="sxs-lookup"><span data-stu-id="ab43c-140">Member name result</span></span>|  
|-------------------------|------------------------|  
|<span data-ttu-id="ab43c-141">Método, propriedade ou evento</span><span class="sxs-lookup"><span data-stu-id="ab43c-141">Method, property, or event</span></span>|<span data-ttu-id="ab43c-142">O nome do método, da propriedade ou do evento em que a chamada foi originada.</span><span class="sxs-lookup"><span data-stu-id="ab43c-142">The name of the method, property, or event from which the call originated.</span></span>|  
|<span data-ttu-id="ab43c-143">Construtor</span><span class="sxs-lookup"><span data-stu-id="ab43c-143">Constructor</span></span>|<span data-ttu-id="ab43c-144">A cadeia de caracteres “.ctor”</span><span class="sxs-lookup"><span data-stu-id="ab43c-144">The string ".ctor"</span></span>|  
|<span data-ttu-id="ab43c-145">Construtor estático</span><span class="sxs-lookup"><span data-stu-id="ab43c-145">Static constructor</span></span>|<span data-ttu-id="ab43c-146">A cadeia de caracteres “.cctor”</span><span class="sxs-lookup"><span data-stu-id="ab43c-146">The string ".cctor"</span></span>|  
|<span data-ttu-id="ab43c-147">Destruidor</span><span class="sxs-lookup"><span data-stu-id="ab43c-147">Destructor</span></span>|<span data-ttu-id="ab43c-148">A cadeia de caracteres "Finalize"</span><span class="sxs-lookup"><span data-stu-id="ab43c-148">The string "Finalize"</span></span>|  
|<span data-ttu-id="ab43c-149">Operadores usuário ou conversões definidos pelo usuário</span><span class="sxs-lookup"><span data-stu-id="ab43c-149">User-defined operators or conversions</span></span>|<span data-ttu-id="ab43c-150">O nome gerado para o membro, por exemplo, “op_Addition”.</span><span class="sxs-lookup"><span data-stu-id="ab43c-150">The generated name for the member, for example, "op_Addition".</span></span>|  
|<span data-ttu-id="ab43c-151">Construtor de atributos</span><span class="sxs-lookup"><span data-stu-id="ab43c-151">Attribute constructor</span></span>|<span data-ttu-id="ab43c-152">O nome do membro ao qual o atributo se aplica.</span><span class="sxs-lookup"><span data-stu-id="ab43c-152">The name of the member to which the attribute is applied.</span></span> <span data-ttu-id="ab43c-153">Se o atributo é qualquer elemento dentro de um membro (como um parâmetro, um valor de retorno, ou um parâmetro de tipo genérico), esse resultado é o nome do membro associado a esse elemento.</span><span class="sxs-lookup"><span data-stu-id="ab43c-153">If the attribute is any element within a member (such as a parameter, a return value, or a generic type parameter), this result is the name of the member that's associated with that element.</span></span>|  
|<span data-ttu-id="ab43c-154">Nenhum membro contentor (por exemplo, nível de assembly ou atributos que são aplicadas aos tipos)</span><span class="sxs-lookup"><span data-stu-id="ab43c-154">No containing member (for example, assembly-level or attributes that are applied to types)</span></span>|<span data-ttu-id="ab43c-155">O valor padrão do parâmetro opcional.</span><span class="sxs-lookup"><span data-stu-id="ab43c-155">The default value of the optional parameter.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ab43c-156">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ab43c-156">See Also</span></span>  
 <span data-ttu-id="ab43c-157">[Atributos (Visual Basic)](../../../visual-basic/language-reference/attributes.md) </span><span class="sxs-lookup"><span data-stu-id="ab43c-157">[Attributes (Visual Basic)](../../../visual-basic/language-reference/attributes.md) </span></span>  
<span data-ttu-id="ab43c-158"> [Atributos comuns (Visual Basic)](../../../visual-basic/programming-guide/concepts/attributes/common-attributes.md) </span><span class="sxs-lookup"><span data-stu-id="ab43c-158"> [Common Attributes (Visual Basic)](../../../visual-basic/programming-guide/concepts/attributes/common-attributes.md) </span></span>  
<span data-ttu-id="ab43c-159"> [Parâmetros opcionais](../../../visual-basic/programming-guide/language-features/procedures/optional-parameters.md) </span><span class="sxs-lookup"><span data-stu-id="ab43c-159"> [Optional Parameters](../../../visual-basic/programming-guide/language-features/procedures/optional-parameters.md) </span></span>  
<span data-ttu-id="ab43c-160"> [Conceitos de programação (Visual Basic)](../../../visual-basic/programming-guide/concepts/index.md)</span><span class="sxs-lookup"><span data-stu-id="ab43c-160"> [Programming Concepts (Visual Basic)](../../../visual-basic/programming-guide/concepts/index.md)</span></span>
