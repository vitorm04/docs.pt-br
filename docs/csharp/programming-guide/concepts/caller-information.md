---
title: Informações do chamador (C#)
ms.date: 07/20/2015
ms.assetid: ffad3d24-2fb7-4641-9124-53b5bc91d339
ms.openlocfilehash: 27f2e7624369061ff3089357c455ae51237e6dfa
ms.sourcegitcommit: ad99773e5e45068ce03b99518008397e1299e0d1
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/23/2018
ms.locfileid: "46586439"
---
# <a name="caller-information-c"></a><span data-ttu-id="ec9fe-102">Informações do chamador (C#)</span><span class="sxs-lookup"><span data-stu-id="ec9fe-102">Caller Information (C#)</span></span>

<span data-ttu-id="ec9fe-103">Ao usar atributos de informações do chamador, você pode obter informações sobre o chamador de um método.</span><span class="sxs-lookup"><span data-stu-id="ec9fe-103">By using Caller Info attributes, you can obtain information about the caller to a method.</span></span> <span data-ttu-id="ec9fe-104">Você pode obter o caminho do arquivo do código-fonte, o número da linha no código-fonte e o nome do membro do chamador.</span><span class="sxs-lookup"><span data-stu-id="ec9fe-104">You can obtain file path of the source code, the line number in the source code, and the member name of the caller.</span></span> <span data-ttu-id="ec9fe-105">Essas informações são úteis para fins de rastreamento, depuração e criação de ferramentas de diagnóstico.</span><span class="sxs-lookup"><span data-stu-id="ec9fe-105">This information is helpful for tracing, debugging, and creating diagnostic tools.</span></span>

<span data-ttu-id="ec9fe-106">Para obter essas informações, você deve usar os atributos que são aplicadas aos parâmetros opcionais, cada qual com um valor padrão.</span><span class="sxs-lookup"><span data-stu-id="ec9fe-106">To obtain this information, you use attributes that are applied to optional parameters, each of which has a default value.</span></span> <span data-ttu-id="ec9fe-107">A tabela a seguir lista os atributos de informações do chamador que são definidos no namespace de <xref:System.Runtime.CompilerServices?displayProperty=nameWithType>:</span><span class="sxs-lookup"><span data-stu-id="ec9fe-107">The following table lists the Caller Info attributes that are defined in the <xref:System.Runtime.CompilerServices?displayProperty=nameWithType> namespace:</span></span>

|<span data-ttu-id="ec9fe-108">Atributo</span><span class="sxs-lookup"><span data-stu-id="ec9fe-108">Attribute</span></span>|<span data-ttu-id="ec9fe-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="ec9fe-109">Description</span></span>|<span data-ttu-id="ec9fe-110">Tipo</span><span class="sxs-lookup"><span data-stu-id="ec9fe-110">Type</span></span>|
|---|---|---|
|<xref:System.Runtime.CompilerServices.CallerFilePathAttribute>|<span data-ttu-id="ec9fe-111">O caminho completo do arquivo de origem que contém o chamador.</span><span class="sxs-lookup"><span data-stu-id="ec9fe-111">Full path of the source file that contains the caller.</span></span> <span data-ttu-id="ec9fe-112">Esse é o caminho do arquivo no momento da compilação.</span><span class="sxs-lookup"><span data-stu-id="ec9fe-112">This is the file path at compile time.</span></span>|`String`|
|<xref:System.Runtime.CompilerServices.CallerLineNumberAttribute>|<span data-ttu-id="ec9fe-113">Número da linha no arquivo fonte no qual o método é chamado.</span><span class="sxs-lookup"><span data-stu-id="ec9fe-113">Line number in the source file at which the method is called.</span></span>|`Integer`|
|<xref:System.Runtime.CompilerServices.CallerMemberNameAttribute>|<span data-ttu-id="ec9fe-114">Nome do método ou da propriedade do chamador.</span><span class="sxs-lookup"><span data-stu-id="ec9fe-114">Method or property name of the caller.</span></span> <span data-ttu-id="ec9fe-115">Consulte [Nomes dos membros](#member-names) mais adiante neste tópico.</span><span class="sxs-lookup"><span data-stu-id="ec9fe-115">See [Member Names](#member-names) later in this topic.</span></span>|`String`|

## <a name="example"></a><span data-ttu-id="ec9fe-116">Exemplo</span><span class="sxs-lookup"><span data-stu-id="ec9fe-116">Example</span></span>

<span data-ttu-id="ec9fe-117">O exemplo a seguir mostra como usar os atributos de informações do chamador.</span><span class="sxs-lookup"><span data-stu-id="ec9fe-117">The following example shows how to use Caller Info attributes.</span></span> <span data-ttu-id="ec9fe-118">Em cada chamada para o método `TraceMessage`, as informações do chamador são substituídas como argumentos para os parâmetros opcionais.</span><span class="sxs-lookup"><span data-stu-id="ec9fe-118">On each call to the `TraceMessage` method, the caller information is substituted as arguments to the optional parameters.</span></span>

```csharp
public void DoProcessing()
{
    TraceMessage("Something happened.");
}

public void TraceMessage(string message,
        [System.Runtime.CompilerServices.CallerMemberName] string memberName = "",
        [System.Runtime.CompilerServices.CallerFilePath] string sourceFilePath = "",
        [System.Runtime.CompilerServices.CallerLineNumber] int sourceLineNumber = 0)
{
    System.Diagnostics.Trace.WriteLine("message: " + message);
    System.Diagnostics.Trace.WriteLine("member name: " + memberName);
    System.Diagnostics.Trace.WriteLine("source file path: " + sourceFilePath);
    System.Diagnostics.Trace.WriteLine("source line number: " + sourceLineNumber);
}

// Sample Output:
//  message: Something happened.
//  member name: DoProcessing
//  source file path: c:\Visual Studio Projects\CallerInfoCS\CallerInfoCS\Form1.cs
//  source line number: 31
```

## <a name="remarks"></a><span data-ttu-id="ec9fe-119">Comentários</span><span class="sxs-lookup"><span data-stu-id="ec9fe-119">Remarks</span></span>

<span data-ttu-id="ec9fe-120">Você deve especificar um valor padrão explícito para cada parâmetro opcional.</span><span class="sxs-lookup"><span data-stu-id="ec9fe-120">You must specify an explicit default value for each optional parameter.</span></span> <span data-ttu-id="ec9fe-121">Você não pode aplicar atributos de informações do chamador aos parâmetros que não são especificados como opcionais.</span><span class="sxs-lookup"><span data-stu-id="ec9fe-121">You can't apply Caller Info attributes to parameters that aren't specified as optional.</span></span>

<span data-ttu-id="ec9fe-122">Os atributos de informações do chamador não tornam um parâmetro opcional.</span><span class="sxs-lookup"><span data-stu-id="ec9fe-122">The Caller Info attributes don't make a parameter optional.</span></span> <span data-ttu-id="ec9fe-123">Em vez disso, eles afetam o valor padrão que é passado quando o argumento é omitido.</span><span class="sxs-lookup"><span data-stu-id="ec9fe-123">Instead, they affect the default value that's passed in when the argument is omitted.</span></span>

<span data-ttu-id="ec9fe-124">Os valores de informações do chamador são emitidos como literais em linguagem intermediária (IL) em tempo de compilação.</span><span class="sxs-lookup"><span data-stu-id="ec9fe-124">Caller Info values are emitted as literals into the Intermediate Language (IL) at compile time.</span></span> <span data-ttu-id="ec9fe-125">Ao contrário dos resultados da propriedade <xref:System.Exception.StackTrace%2A> para exceções, os resultados não são afetados por ofuscamento.</span><span class="sxs-lookup"><span data-stu-id="ec9fe-125">Unlike the results of the <xref:System.Exception.StackTrace%2A> property for exceptions, the results aren't affected by obfuscation.</span></span>

<span data-ttu-id="ec9fe-126">Você pode fornecer explicitamente os argumentos opcionais para controlar as informações do chamador ou ocultá-las.</span><span class="sxs-lookup"><span data-stu-id="ec9fe-126">You can explicitly supply the optional arguments to control the caller information or to hide caller information.</span></span>

### <a name="member-names"></a><span data-ttu-id="ec9fe-127">Nomes dos membros</span><span class="sxs-lookup"><span data-stu-id="ec9fe-127">Member names</span></span>

<span data-ttu-id="ec9fe-128">Você pode usar o atributo `CallerMemberName` para evitar especificar o nome do membro como um argumento `String` ao método chamado.</span><span class="sxs-lookup"><span data-stu-id="ec9fe-128">You can use the `CallerMemberName` attribute to avoid specifying the member name as a `String` argument to the called method.</span></span> <span data-ttu-id="ec9fe-129">Ao usar essa técnica, você evita o problema de que a **Refatoração de Renomeação** não altera os valores de `String`.</span><span class="sxs-lookup"><span data-stu-id="ec9fe-129">By using this technique, you avoid the problem that **Rename Refactoring** doesn't change the `String` values.</span></span> <span data-ttu-id="ec9fe-130">Esse benefício é especialmente útil para as seguintes tarefas:</span><span class="sxs-lookup"><span data-stu-id="ec9fe-130">This benefit is especially useful for the following tasks:</span></span>

- <span data-ttu-id="ec9fe-131">Usar rotinas de rastreamento e diagnóstico.</span><span class="sxs-lookup"><span data-stu-id="ec9fe-131">Using tracing and diagnostic routines.</span></span>

- <span data-ttu-id="ec9fe-132">Implementando a interface <xref:System.ComponentModel.INotifyPropertyChanged> ao associar dados.</span><span class="sxs-lookup"><span data-stu-id="ec9fe-132">Implementing the <xref:System.ComponentModel.INotifyPropertyChanged> interface when binding data.</span></span> <span data-ttu-id="ec9fe-133">Essa interface permite que a propriedade de um objeto notifique um controle associado sobre a alteração da propriedade de modo que o controle possa exibir as informações atualizadas.</span><span class="sxs-lookup"><span data-stu-id="ec9fe-133">This interface allows the property of an object to notify a bound control that the property has changed, so that the control can display the updated information.</span></span> <span data-ttu-id="ec9fe-134">Sem o atributo `CallerMemberName`, você deve especificar o nome da propriedade como um literal.</span><span class="sxs-lookup"><span data-stu-id="ec9fe-134">Without the `CallerMemberName` attribute, you must specify the property name as a literal.</span></span>

<span data-ttu-id="ec9fe-135">O gráfico a seguir mostra os nomes de membros que são retornados quando você usa o atributo `CallerMemberName`.</span><span class="sxs-lookup"><span data-stu-id="ec9fe-135">The following chart shows the member names that are returned when you use the `CallerMemberName` attribute.</span></span>

|<span data-ttu-id="ec9fe-136">As chamadas ocorrem em</span><span class="sxs-lookup"><span data-stu-id="ec9fe-136">Calls occurs within</span></span>|<span data-ttu-id="ec9fe-137">Resultado de nome de membro</span><span class="sxs-lookup"><span data-stu-id="ec9fe-137">Member name result</span></span>|
|-|-|
|<span data-ttu-id="ec9fe-138">Método, propriedade ou evento</span><span class="sxs-lookup"><span data-stu-id="ec9fe-138">Method, property, or event</span></span>|<span data-ttu-id="ec9fe-139">O nome do método, da propriedade ou do evento em que a chamada foi originada.</span><span class="sxs-lookup"><span data-stu-id="ec9fe-139">The name of the method, property, or event from which the call originated.</span></span>|
|<span data-ttu-id="ec9fe-140">Construtor</span><span class="sxs-lookup"><span data-stu-id="ec9fe-140">Constructor</span></span>|<span data-ttu-id="ec9fe-141">A cadeia de caracteres “.ctor”</span><span class="sxs-lookup"><span data-stu-id="ec9fe-141">The string ".ctor"</span></span>|
|<span data-ttu-id="ec9fe-142">Construtor estático</span><span class="sxs-lookup"><span data-stu-id="ec9fe-142">Static constructor</span></span>|<span data-ttu-id="ec9fe-143">A cadeia de caracteres “.cctor”</span><span class="sxs-lookup"><span data-stu-id="ec9fe-143">The string ".cctor"</span></span>|
|<span data-ttu-id="ec9fe-144">Destruidor</span><span class="sxs-lookup"><span data-stu-id="ec9fe-144">Destructor</span></span>|<span data-ttu-id="ec9fe-145">A cadeia de caracteres "Finalize"</span><span class="sxs-lookup"><span data-stu-id="ec9fe-145">The string "Finalize"</span></span>|
|<span data-ttu-id="ec9fe-146">Operadores usuário ou conversões definidos pelo usuário</span><span class="sxs-lookup"><span data-stu-id="ec9fe-146">User-defined operators or conversions</span></span>|<span data-ttu-id="ec9fe-147">O nome gerado para o membro, por exemplo, “op_Addition”.</span><span class="sxs-lookup"><span data-stu-id="ec9fe-147">The generated name for the member, for example, "op_Addition".</span></span>|
|<span data-ttu-id="ec9fe-148">Construtor de atributos</span><span class="sxs-lookup"><span data-stu-id="ec9fe-148">Attribute constructor</span></span>|<span data-ttu-id="ec9fe-149">O nome do membro ao qual o atributo se aplica.</span><span class="sxs-lookup"><span data-stu-id="ec9fe-149">The name of the member to which the attribute is applied.</span></span> <span data-ttu-id="ec9fe-150">Se o atributo é qualquer elemento dentro de um membro (como um parâmetro, um valor de retorno, ou um parâmetro de tipo genérico), esse resultado é o nome do membro associado a esse elemento.</span><span class="sxs-lookup"><span data-stu-id="ec9fe-150">If the attribute is any element within a member (such as a parameter, a return value, or a generic type parameter), this result is the name of the member that's associated with that element.</span></span>|
|<span data-ttu-id="ec9fe-151">Nenhum membro contentor (por exemplo, nível de assembly ou atributos que são aplicadas aos tipos)</span><span class="sxs-lookup"><span data-stu-id="ec9fe-151">No containing member (for example, assembly-level or attributes that are applied to types)</span></span>|<span data-ttu-id="ec9fe-152">O valor padrão do parâmetro opcional.</span><span class="sxs-lookup"><span data-stu-id="ec9fe-152">The default value of the optional parameter.</span></span>|

## <a name="see-also"></a><span data-ttu-id="ec9fe-153">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ec9fe-153">See also</span></span>

- [<span data-ttu-id="ec9fe-154">Atributos (C#)</span><span class="sxs-lookup"><span data-stu-id="ec9fe-154">Attributes (C#)</span></span>](../../../csharp/programming-guide/concepts/attributes/index.md)
- [<span data-ttu-id="ec9fe-155">Atributos comuns (C#)</span><span class="sxs-lookup"><span data-stu-id="ec9fe-155">Common Attributes (C#)</span></span>](../../../csharp/programming-guide/concepts/attributes/common-attributes.md)
- [<span data-ttu-id="ec9fe-156">Argumentos nomeados e opcionais</span><span class="sxs-lookup"><span data-stu-id="ec9fe-156">Named and Optional Arguments</span></span>](../../../csharp/programming-guide/classes-and-structs/named-and-optional-arguments.md)
- [<span data-ttu-id="ec9fe-157">Conceitos de programação (C#)</span><span class="sxs-lookup"><span data-stu-id="ec9fe-157">Programming Concepts (C#)</span></span>](../../../csharp/programming-guide/concepts/index.md)
