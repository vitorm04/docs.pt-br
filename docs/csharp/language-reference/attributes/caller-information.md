---
title: 'C# Atributos reservados: Rastreamento de informações do chamador'
ms.date: 04/09/2020
description: Esses atributos instruem o compilador a gerar informações sobre o código que chama um membro. Você usa o CallerFilePath, CallerLineNumber e CallerMemberName para fornecer informações detalhadas de rastreamento
ms.openlocfilehash: ee061d4cae35bdcc0b89007e360e94fee8c5f87c
ms.sourcegitcommit: c91110ef6ee3fedb591f3d628dc17739c4a7071e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/15/2020
ms.locfileid: "81389873"
---
# <a name="reserved-attributes-determine-caller-information"></a><span data-ttu-id="ed28d-104">Atributos reservados: Determine as informações do chamador</span><span class="sxs-lookup"><span data-stu-id="ed28d-104">Reserved attributes: Determine caller information</span></span>

<span data-ttu-id="ed28d-105">Usando atributos de informação, você obtém informações sobre o chamador para um método.</span><span class="sxs-lookup"><span data-stu-id="ed28d-105">Using info attributes, you obtain information about the caller to a method.</span></span> <span data-ttu-id="ed28d-106">Você obtém o caminho do arquivo do código fonte, o número da linha no código-fonte e o nome do membro do chamador.</span><span class="sxs-lookup"><span data-stu-id="ed28d-106">You obtain the file path of the source code, the line number in the source code, and the member name of the caller.</span></span> <span data-ttu-id="ed28d-107">Para obter informações do chamador do membro, você usa os atributos que são aplicados aos parâmetros opcionais.</span><span class="sxs-lookup"><span data-stu-id="ed28d-107">To obtain member caller information, you use attributes that are applied to optional parameters.</span></span> <span data-ttu-id="ed28d-108">Cada parâmetro opcional especifica um valor padrão.</span><span class="sxs-lookup"><span data-stu-id="ed28d-108">Each optional parameter specifies a default value.</span></span> <span data-ttu-id="ed28d-109">A tabela a seguir lista os atributos de informações do chamador que são definidos no namespace de <xref:System.Runtime.CompilerServices?displayProperty=nameWithType>:</span><span class="sxs-lookup"><span data-stu-id="ed28d-109">The following table lists the Caller Info attributes that are defined in the <xref:System.Runtime.CompilerServices?displayProperty=nameWithType> namespace:</span></span>

|<span data-ttu-id="ed28d-110">Atributo</span><span class="sxs-lookup"><span data-stu-id="ed28d-110">Attribute</span></span>|<span data-ttu-id="ed28d-111">Descrição</span><span class="sxs-lookup"><span data-stu-id="ed28d-111">Description</span></span>|<span data-ttu-id="ed28d-112">Type</span><span class="sxs-lookup"><span data-stu-id="ed28d-112">Type</span></span>|
|---|---|---|
|<xref:System.Runtime.CompilerServices.CallerFilePathAttribute>|<span data-ttu-id="ed28d-113">O caminho completo do arquivo de origem que contém o chamador.</span><span class="sxs-lookup"><span data-stu-id="ed28d-113">Full path of the source file that contains the caller.</span></span> <span data-ttu-id="ed28d-114">O caminho completo é o caminho na hora da compilação.</span><span class="sxs-lookup"><span data-stu-id="ed28d-114">The full path is the path at compile time.</span></span>|`String`|
|<xref:System.Runtime.CompilerServices.CallerLineNumberAttribute>|<span data-ttu-id="ed28d-115">Número de linha no arquivo de origem do qual o método é chamado.</span><span class="sxs-lookup"><span data-stu-id="ed28d-115">Line number in the source file from which the method is called.</span></span>|`Integer`|
|<xref:System.Runtime.CompilerServices.CallerMemberNameAttribute>|<span data-ttu-id="ed28d-116">Nome do método ou nome da propriedade do chamador.</span><span class="sxs-lookup"><span data-stu-id="ed28d-116">Method name or property name of the caller.</span></span>|`String`|

<span data-ttu-id="ed28d-117">Essas informações ajudam você a escrever rastreamento, depuração e criar ferramentas de diagnóstico.</span><span class="sxs-lookup"><span data-stu-id="ed28d-117">This information helps you write tracing, debugging, and create diagnostic tools.</span></span> <span data-ttu-id="ed28d-118">O exemplo a seguir mostra como usar os atributos de informações do chamador.</span><span class="sxs-lookup"><span data-stu-id="ed28d-118">The following example shows how to use caller info attributes.</span></span> <span data-ttu-id="ed28d-119">Em cada chamada para o método `TraceMessage`, as informações do chamador são substituídas como argumentos para os parâmetros opcionais.</span><span class="sxs-lookup"><span data-stu-id="ed28d-119">On each call to the `TraceMessage` method, the caller information is substituted as arguments to the optional parameters.</span></span>

```csharp
public void DoProcessing()
{
    TraceMessage("Something happened.");
}

public void TraceMessage(string message,
        [CallerMemberName] string memberName = "",
        [CallerFilePath] string sourceFilePath = "",
        [CallerLineNumber] int sourceLineNumber = 0)
{
    Trace.WriteLine("message: " + message);
    Trace.WriteLine("member name: " + memberName);
    Trace.WriteLine("source file path: " + sourceFilePath);
    Trace.WriteLine("source line number: " + sourceLineNumber);
}

// Sample Output:
//  message: Something happened.
//  member name: DoProcessing
//  source file path: c:\Visual Studio Projects\CallerInfoCS\CallerInfoCS\Form1.cs
//  source line number: 31
```

<span data-ttu-id="ed28d-120">Você especifica um valor padrão explícito para cada parâmetro opcional.</span><span class="sxs-lookup"><span data-stu-id="ed28d-120">You specify an explicit default value for each optional parameter.</span></span> <span data-ttu-id="ed28d-121">Você não pode aplicar atributos de informações de chamadas a parâmetros que não são especificados como opcionais.</span><span class="sxs-lookup"><span data-stu-id="ed28d-121">You can't apply caller info attributes to parameters that aren't specified as optional.</span></span> <span data-ttu-id="ed28d-122">Os atributos de informações do chamador não tornam um parâmetro opcional.</span><span class="sxs-lookup"><span data-stu-id="ed28d-122">The caller info attributes don't make a parameter optional.</span></span> <span data-ttu-id="ed28d-123">Em vez disso, eles afetam o valor padrão que é passado quando o argumento é omitido.</span><span class="sxs-lookup"><span data-stu-id="ed28d-123">Instead, they affect the default value that's passed in when the argument is omitted.</span></span> <span data-ttu-id="ed28d-124">Os valores de informações do chamador são emitidos como literais na Língua Intermediária (IL) no momento da compilação.</span><span class="sxs-lookup"><span data-stu-id="ed28d-124">Caller info values are emitted as literals into the Intermediate Language (IL) at compile time.</span></span> <span data-ttu-id="ed28d-125">Ao contrário dos resultados da propriedade <xref:System.Exception.StackTrace%2A> para exceções, os resultados não são afetados por ofuscamento.</span><span class="sxs-lookup"><span data-stu-id="ed28d-125">Unlike the results of the <xref:System.Exception.StackTrace%2A> property for exceptions, the results aren't affected by obfuscation.</span></span> <span data-ttu-id="ed28d-126">Você pode fornecer explicitamente os argumentos opcionais para controlar as informações do chamador ou ocultá-las.</span><span class="sxs-lookup"><span data-stu-id="ed28d-126">You can explicitly supply the optional arguments to control the caller information or to hide caller information.</span></span>

### <a name="member-names"></a><span data-ttu-id="ed28d-127">Nomes dos membros</span><span class="sxs-lookup"><span data-stu-id="ed28d-127">Member names</span></span>

<span data-ttu-id="ed28d-128">Você pode usar o atributo `CallerMemberName` para evitar especificar o nome do membro como um argumento `String` ao método chamado.</span><span class="sxs-lookup"><span data-stu-id="ed28d-128">You can use the `CallerMemberName` attribute to avoid specifying the member name as a `String` argument to the called method.</span></span> <span data-ttu-id="ed28d-129">Ao usar essa técnica, você evita o problema de que a **Refatoração de Renomeação** não altera os valores de `String`.</span><span class="sxs-lookup"><span data-stu-id="ed28d-129">By using this technique, you avoid the problem that **Rename Refactoring** doesn't change the `String` values.</span></span> <span data-ttu-id="ed28d-130">Esse benefício é especialmente útil para as seguintes tarefas:</span><span class="sxs-lookup"><span data-stu-id="ed28d-130">This benefit is especially useful for the following tasks:</span></span>

- <span data-ttu-id="ed28d-131">Usar rotinas de rastreamento e diagnóstico.</span><span class="sxs-lookup"><span data-stu-id="ed28d-131">Using tracing and diagnostic routines.</span></span>
- <span data-ttu-id="ed28d-132">Implementando a interface <xref:System.ComponentModel.INotifyPropertyChanged> ao associar dados.</span><span class="sxs-lookup"><span data-stu-id="ed28d-132">Implementing the <xref:System.ComponentModel.INotifyPropertyChanged> interface when binding data.</span></span> <span data-ttu-id="ed28d-133">Essa interface permite que a propriedade de um objeto notifique um controle associado sobre a alteração da propriedade de modo que o controle possa exibir as informações atualizadas.</span><span class="sxs-lookup"><span data-stu-id="ed28d-133">This interface allows the property of an object to notify a bound control that the property has changed, so that the control can display the updated information.</span></span> <span data-ttu-id="ed28d-134">Sem o atributo `CallerMemberName`, você deve especificar o nome da propriedade como um literal.</span><span class="sxs-lookup"><span data-stu-id="ed28d-134">Without the `CallerMemberName` attribute, you must specify the property name as a literal.</span></span>

<span data-ttu-id="ed28d-135">O gráfico a seguir mostra os nomes de membros que são retornados quando você usa o atributo `CallerMemberName`.</span><span class="sxs-lookup"><span data-stu-id="ed28d-135">The following chart shows the member names that are returned when you use the `CallerMemberName` attribute.</span></span>

|<span data-ttu-id="ed28d-136">Chamadas ocorrem dentro</span><span class="sxs-lookup"><span data-stu-id="ed28d-136">Calls occur within</span></span>|<span data-ttu-id="ed28d-137">Resultado de nome de membro</span><span class="sxs-lookup"><span data-stu-id="ed28d-137">Member name result</span></span>|
|-|-|
|<span data-ttu-id="ed28d-138">Método, propriedade ou evento</span><span class="sxs-lookup"><span data-stu-id="ed28d-138">Method, property, or event</span></span>|<span data-ttu-id="ed28d-139">O nome do método, da propriedade ou do evento em que a chamada foi originada.</span><span class="sxs-lookup"><span data-stu-id="ed28d-139">The name of the method, property, or event from which the call originated.</span></span>|
|<span data-ttu-id="ed28d-140">Construtor</span><span class="sxs-lookup"><span data-stu-id="ed28d-140">Constructor</span></span>|<span data-ttu-id="ed28d-141">A cadeia de caracteres “.ctor”</span><span class="sxs-lookup"><span data-stu-id="ed28d-141">The string ".ctor"</span></span>|
|<span data-ttu-id="ed28d-142">Construtor estático</span><span class="sxs-lookup"><span data-stu-id="ed28d-142">Static constructor</span></span>|<span data-ttu-id="ed28d-143">A cadeia de caracteres “.cctor”</span><span class="sxs-lookup"><span data-stu-id="ed28d-143">The string ".cctor"</span></span>|
|<span data-ttu-id="ed28d-144">Destruidor</span><span class="sxs-lookup"><span data-stu-id="ed28d-144">Destructor</span></span>|<span data-ttu-id="ed28d-145">A cadeia de caracteres "Finalize"</span><span class="sxs-lookup"><span data-stu-id="ed28d-145">The string "Finalize"</span></span>|
|<span data-ttu-id="ed28d-146">Operadores usuário ou conversões definidos pelo usuário</span><span class="sxs-lookup"><span data-stu-id="ed28d-146">User-defined operators or conversions</span></span>|<span data-ttu-id="ed28d-147">O nome gerado para o membro, por exemplo, “op_Addition”.</span><span class="sxs-lookup"><span data-stu-id="ed28d-147">The generated name for the member, for example, "op_Addition".</span></span>|
|<span data-ttu-id="ed28d-148">Construtor de atributos</span><span class="sxs-lookup"><span data-stu-id="ed28d-148">Attribute constructor</span></span>|<span data-ttu-id="ed28d-149">O nome do método ou propriedade ao qual o atributo se aplica.</span><span class="sxs-lookup"><span data-stu-id="ed28d-149">The name of the method or property to which the attribute is applied.</span></span> <span data-ttu-id="ed28d-150">Se o atributo é qualquer elemento dentro de um membro (como um parâmetro, um valor de retorno, ou um parâmetro de tipo genérico), esse resultado é o nome do membro associado a esse elemento.</span><span class="sxs-lookup"><span data-stu-id="ed28d-150">If the attribute is any element within a member (such as a parameter, a return value, or a generic type parameter), this result is the name of the member that's associated with that element.</span></span>|
|<span data-ttu-id="ed28d-151">Nenhum membro contentor (por exemplo, nível de assembly ou atributos que são aplicadas aos tipos)</span><span class="sxs-lookup"><span data-stu-id="ed28d-151">No containing member (for example, assembly-level or attributes that are applied to types)</span></span>|<span data-ttu-id="ed28d-152">O valor padrão do parâmetro opcional.</span><span class="sxs-lookup"><span data-stu-id="ed28d-152">The default value of the optional parameter.</span></span>|

## <a name="see-also"></a><span data-ttu-id="ed28d-153">Confira também</span><span class="sxs-lookup"><span data-stu-id="ed28d-153">See also</span></span>

- [<span data-ttu-id="ed28d-154">Argumentos nomeados e opcionais</span><span class="sxs-lookup"><span data-stu-id="ed28d-154">Named and Optional Arguments</span></span>](../../programming-guide/classes-and-structs/named-and-optional-arguments.md)
- <xref:System.Reflection>
- <xref:System.Attribute>
- [<span data-ttu-id="ed28d-155">Atributos</span><span class="sxs-lookup"><span data-stu-id="ed28d-155">Attributes</span></span>](../../../standard/attributes/index.md)
