---
title: Informações do chamador (F#)
description: Descreve como usar atributos de argumento de informações do chamador para obter informações do chamador de um método.
ms.date: 04/25/2017
ms.openlocfilehash: 0f2f4b16804d9156d234cc29d1f72ebe80a5b556
ms.sourcegitcommit: db8b83057d052c1f9f249d128b08d4423af0f7c2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/02/2018
ms.locfileid: "47216364"
---
# <a name="caller-information"></a><span data-ttu-id="69b35-103">Informações do chamador</span><span class="sxs-lookup"><span data-stu-id="69b35-103">Caller information</span></span>

<span data-ttu-id="69b35-104">Ao usar atributos de informações do chamador, você pode obter informações sobre o chamador de um método.</span><span class="sxs-lookup"><span data-stu-id="69b35-104">By using Caller Info attributes, you can obtain information about the caller to a method.</span></span> <span data-ttu-id="69b35-105">Você pode obter o caminho do arquivo do código-fonte, o número da linha no código-fonte e o nome do membro do chamador.</span><span class="sxs-lookup"><span data-stu-id="69b35-105">You can obtain file path of the source code, the line number in the source code, and the member name of the caller.</span></span> <span data-ttu-id="69b35-106">Essas informações são úteis para fins de rastreamento, depuração e criação de ferramentas de diagnóstico.</span><span class="sxs-lookup"><span data-stu-id="69b35-106">This information is helpful for tracing, debugging, and creating diagnostic tools.</span></span>

<span data-ttu-id="69b35-107">Para obter essas informações, você deve usar os atributos que são aplicadas aos parâmetros opcionais, cada qual com um valor padrão.</span><span class="sxs-lookup"><span data-stu-id="69b35-107">To obtain this information, you use attributes that are applied to optional parameters, each of which has a default value.</span></span> <span data-ttu-id="69b35-108">A tabela a seguir lista os atributos de informações do chamador que são definidos na [CompilerServices](/dotnet/api/system.runtime.compilerservices) namespace:</span><span class="sxs-lookup"><span data-stu-id="69b35-108">The following table lists the Caller Info attributes that are defined in the [System.Runtime.CompilerServices](/dotnet/api/system.runtime.compilerservices) namespace:</span></span>

|<span data-ttu-id="69b35-109">Atributo</span><span class="sxs-lookup"><span data-stu-id="69b35-109">Attribute</span></span>|<span data-ttu-id="69b35-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="69b35-110">Description</span></span>|<span data-ttu-id="69b35-111">Tipo</span><span class="sxs-lookup"><span data-stu-id="69b35-111">Type</span></span>|
|---------|-----------|----|
|[<span data-ttu-id="69b35-112">CallerFilePath</span><span class="sxs-lookup"><span data-stu-id="69b35-112">CallerFilePath</span></span>](/dotnet/api/system.runtime.compilerservices.callerfilepathattribute)|<span data-ttu-id="69b35-113">O caminho completo do arquivo de origem que contém o chamador.</span><span class="sxs-lookup"><span data-stu-id="69b35-113">Full path of the source file that contains the caller.</span></span> <span data-ttu-id="69b35-114">Esse é o caminho do arquivo no momento da compilação.</span><span class="sxs-lookup"><span data-stu-id="69b35-114">This is the file path at compile time.</span></span>|`String`
|[<span data-ttu-id="69b35-115">CallerLineNumber</span><span class="sxs-lookup"><span data-stu-id="69b35-115">CallerLineNumber</span></span>](/dotnet/api/system.runtime.compilerservices.callerlinenumberattribute)|<span data-ttu-id="69b35-116">Número da linha no arquivo fonte no qual o método é chamado.</span><span class="sxs-lookup"><span data-stu-id="69b35-116">Line number in the source file at which the method is called.</span></span>|`Integer`|
|[<span data-ttu-id="69b35-117">CallerMemberName</span><span class="sxs-lookup"><span data-stu-id="69b35-117">CallerMemberName</span></span>](/dotnet/api/system.runtime.compilerservices.callermembernameattribute)|<span data-ttu-id="69b35-118">Nome do método ou da propriedade do chamador.</span><span class="sxs-lookup"><span data-stu-id="69b35-118">Method or property name of the caller.</span></span> <span data-ttu-id="69b35-119">Consulte a seção de nomes de membros mais adiante neste tópico.</span><span class="sxs-lookup"><span data-stu-id="69b35-119">See the Member Names section later in this topic.</span></span>|`String`|

## <a name="example"></a><span data-ttu-id="69b35-120">Exemplo</span><span class="sxs-lookup"><span data-stu-id="69b35-120">Example</span></span>

<span data-ttu-id="69b35-121">O exemplo a seguir mostra como você pode usar esses atributos para rastrear um chamador.</span><span class="sxs-lookup"><span data-stu-id="69b35-121">The following example shows how you might use these attributes to trace a caller.</span></span>

```fsharp
open System.Diagnostics
open System.Runtime.CompilerServices

type Tracer() =
    member __.DoTrace(msg: string,
                      [<CallerMemberName>] ?memberName: string,
                      [<CallerFilePath>] ?path: string
                      [<CallerLineNumber>] ?line: int) =
        Trace.WriteLine(sprintf "Message: %s" message)
        match (memberName, path, line) with
        | Some m, Some p, Some l ->
            Trace.WriteLine(sprintf "Member name: %s" m)
            Trace.WriteLine(sprintf "Source file path: %s" p)
            Trace.WriteLine(sprintf "Source line number: %d" l)
        | _,_,_ -> ()
```

## <a name="remarks"></a><span data-ttu-id="69b35-122">Comentários</span><span class="sxs-lookup"><span data-stu-id="69b35-122">Remarks</span></span>

<span data-ttu-id="69b35-123">Atributos de informações do chamador só podem ser aplicados aos parâmetros opcionais.</span><span class="sxs-lookup"><span data-stu-id="69b35-123">Caller Info attributes can only be applied to optional parameters.</span></span> <span data-ttu-id="69b35-124">Você deve fornecer um valor explícito para cada parâmetro opcional.</span><span class="sxs-lookup"><span data-stu-id="69b35-124">You must supply an explicit value for each optional parameter.</span></span> <span data-ttu-id="69b35-125">Os atributos de informações do chamador com que o compilador gravar o valor apropriado para cada parâmetro opcional decorado com um atributo de informações do chamador.</span><span class="sxs-lookup"><span data-stu-id="69b35-125">The Caller Info attributes cause the compiler to write the proper value for each optional parameter decorated with a Caller Info attribute.</span></span>

<span data-ttu-id="69b35-126">Os valores de informações do chamador são emitidos como literais em linguagem intermediária (IL) em tempo de compilação.</span><span class="sxs-lookup"><span data-stu-id="69b35-126">Caller Info values are emitted as literals into the Intermediate Language (IL) at compile time.</span></span> <span data-ttu-id="69b35-127">Ao contrário dos resultados do [StackTrace](/dotnet/api/system.diagnostics.stacktrace) propriedade para exceções, os resultados não são afetados por ofuscação.</span><span class="sxs-lookup"><span data-stu-id="69b35-127">Unlike the results of the [StackTrace](/dotnet/api/system.diagnostics.stacktrace) property for exceptions, the results aren't affected by obfuscation.</span></span>

<span data-ttu-id="69b35-128">Você pode fornecer explicitamente os argumentos opcionais para controlar as informações do chamador ou ocultá-las.</span><span class="sxs-lookup"><span data-stu-id="69b35-128">You can explicitly supply the optional arguments to control the caller information or to hide caller information.</span></span>

## <a name="member-names"></a><span data-ttu-id="69b35-129">Nomes dos membros</span><span class="sxs-lookup"><span data-stu-id="69b35-129">Member names</span></span>

<span data-ttu-id="69b35-130">Você pode usar o [ `CallerMemberName` ](/dotnet/api/system.runtime.compilerservices.callermembernameattribute) atributo para evitar especificar o nome do membro como um `String` argumento para o método chamado.</span><span class="sxs-lookup"><span data-stu-id="69b35-130">You can use the [`CallerMemberName`](/dotnet/api/system.runtime.compilerservices.callermembernameattribute) attribute to avoid specifying the member name as a `String` argument to the called method.</span></span> <span data-ttu-id="69b35-131">Ao usar essa técnica, você evita que o problema que refatoração de renomeação não altera o `String` valores.</span><span class="sxs-lookup"><span data-stu-id="69b35-131">By using this technique, you avoid the problem that Rename Refactoring doesn't change the `String` values.</span></span> <span data-ttu-id="69b35-132">Esse benefício é especialmente útil para as seguintes tarefas:</span><span class="sxs-lookup"><span data-stu-id="69b35-132">This benefit is especially useful for the following tasks:</span></span>

* <span data-ttu-id="69b35-133">Usar rotinas de rastreamento e diagnóstico.</span><span class="sxs-lookup"><span data-stu-id="69b35-133">Using tracing and diagnostic routines.</span></span>
* <span data-ttu-id="69b35-134">Implementando o [INotifyPropertyChanged](/dotnet/api/system.componentmodel.inotifypropertychanged) interface quando a associação de dados.</span><span class="sxs-lookup"><span data-stu-id="69b35-134">Implementing the [INotifyPropertyChanged](/dotnet/api/system.componentmodel.inotifypropertychanged) interface when binding data.</span></span> <span data-ttu-id="69b35-135">Essa interface permite que a propriedade de um objeto notifique um controle associado sobre a alteração da propriedade de modo que o controle possa exibir as informações atualizadas.</span><span class="sxs-lookup"><span data-stu-id="69b35-135">This interface allows the property of an object to notify a bound control that the property has changed, so that the control can display the updated information.</span></span> <span data-ttu-id="69b35-136">Sem o [ `CallerMemberName` ](/dotnet/api/system.runtime.compilerservices.callermembernameattribute) atributo, você deve especificar o nome da propriedade como um literal.</span><span class="sxs-lookup"><span data-stu-id="69b35-136">Without the [`CallerMemberName`](/dotnet/api/system.runtime.compilerservices.callermembernameattribute) attribute, you must specify the property name as a literal.</span></span>

<span data-ttu-id="69b35-137">O gráfico a seguir mostra o membro nomes que são retornados quando você usa o atributo CallerMemberName.</span><span class="sxs-lookup"><span data-stu-id="69b35-137">The following chart shows the member names that are returned when you use the CallerMemberName attribute.</span></span>

|<span data-ttu-id="69b35-138">As chamadas ocorrem em</span><span class="sxs-lookup"><span data-stu-id="69b35-138">Calls occurs within</span></span>|<span data-ttu-id="69b35-139">Resultado de nome de membro</span><span class="sxs-lookup"><span data-stu-id="69b35-139">Member name result</span></span>|
|-------------------|------------------|
|<span data-ttu-id="69b35-140">Método, propriedade ou evento</span><span class="sxs-lookup"><span data-stu-id="69b35-140">Method, property, or event</span></span>|<span data-ttu-id="69b35-141">O nome do método, da propriedade ou do evento em que a chamada foi originada.</span><span class="sxs-lookup"><span data-stu-id="69b35-141">The name of the method, property, or event from which the call originated.</span></span>|
|<span data-ttu-id="69b35-142">Construtor</span><span class="sxs-lookup"><span data-stu-id="69b35-142">Constructor</span></span>|<span data-ttu-id="69b35-143">A cadeia de caracteres “.ctor”</span><span class="sxs-lookup"><span data-stu-id="69b35-143">The string ".ctor"</span></span>|
|<span data-ttu-id="69b35-144">Construtor estático</span><span class="sxs-lookup"><span data-stu-id="69b35-144">Static constructor</span></span>|<span data-ttu-id="69b35-145">A cadeia de caracteres “.cctor”</span><span class="sxs-lookup"><span data-stu-id="69b35-145">The string ".cctor"</span></span>|
|<span data-ttu-id="69b35-146">Destruidor</span><span class="sxs-lookup"><span data-stu-id="69b35-146">Destructor</span></span>|<span data-ttu-id="69b35-147">A cadeia de caracteres "Finalize"</span><span class="sxs-lookup"><span data-stu-id="69b35-147">The string "Finalize"</span></span>|
|<span data-ttu-id="69b35-148">Operadores usuário ou conversões definidos pelo usuário</span><span class="sxs-lookup"><span data-stu-id="69b35-148">User-defined operators or conversions</span></span>|<span data-ttu-id="69b35-149">O nome gerado para o membro, por exemplo, “op_Addition”.</span><span class="sxs-lookup"><span data-stu-id="69b35-149">The generated name for the member, for example, "op_Addition".</span></span>|
|<span data-ttu-id="69b35-150">Construtor de atributos</span><span class="sxs-lookup"><span data-stu-id="69b35-150">Attribute constructor</span></span>|<span data-ttu-id="69b35-151">O nome do membro ao qual o atributo se aplica.</span><span class="sxs-lookup"><span data-stu-id="69b35-151">The name of the member to which the attribute is applied.</span></span> <span data-ttu-id="69b35-152">Se o atributo é qualquer elemento dentro de um membro (como um parâmetro, um valor de retorno, ou um parâmetro de tipo genérico), esse resultado é o nome do membro associado a esse elemento.</span><span class="sxs-lookup"><span data-stu-id="69b35-152">If the attribute is any element within a member (such as a parameter, a return value, or a generic type parameter), this result is the name of the member that's associated with that element.</span></span>|
|<span data-ttu-id="69b35-153">Nenhum membro contentor (por exemplo, nível de assembly ou atributos que são aplicadas aos tipos)</span><span class="sxs-lookup"><span data-stu-id="69b35-153">No containing member (for example, assembly-level or attributes that are applied to types)</span></span>|<span data-ttu-id="69b35-154">O valor padrão do parâmetro opcional.</span><span class="sxs-lookup"><span data-stu-id="69b35-154">The default value of the optional parameter.</span></span>|

## <a name="see-also"></a><span data-ttu-id="69b35-155">Consulte também</span><span class="sxs-lookup"><span data-stu-id="69b35-155">See also</span></span>

- [<span data-ttu-id="69b35-156">Atributos</span><span class="sxs-lookup"><span data-stu-id="69b35-156">Attributes</span></span>](attributes.md)  
- [<span data-ttu-id="69b35-157">Argumentos nomeados</span><span class="sxs-lookup"><span data-stu-id="69b35-157">Named arguments</span></span>](parameters-and-arguments.md#named-arguments)  
- [<span data-ttu-id="69b35-158">Parâmetros opcionais</span><span class="sxs-lookup"><span data-stu-id="69b35-158">Optional parameters</span></span>](parameters-and-arguments.md#optional-parameters)  
