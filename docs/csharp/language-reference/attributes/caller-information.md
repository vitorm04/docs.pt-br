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
# <a name="reserved-attributes-determine-caller-information"></a>Atributos reservados: Determine as informações do chamador

Usando atributos de informação, você obtém informações sobre o chamador para um método. Você obtém o caminho do arquivo do código fonte, o número da linha no código-fonte e o nome do membro do chamador. Para obter informações do chamador do membro, você usa os atributos que são aplicados aos parâmetros opcionais. Cada parâmetro opcional especifica um valor padrão. A tabela a seguir lista os atributos de informações do chamador que são definidos no namespace de <xref:System.Runtime.CompilerServices?displayProperty=nameWithType>:

|Atributo|Descrição|Type|
|---|---|---|
|<xref:System.Runtime.CompilerServices.CallerFilePathAttribute>|O caminho completo do arquivo de origem que contém o chamador. O caminho completo é o caminho na hora da compilação.|`String`|
|<xref:System.Runtime.CompilerServices.CallerLineNumberAttribute>|Número de linha no arquivo de origem do qual o método é chamado.|`Integer`|
|<xref:System.Runtime.CompilerServices.CallerMemberNameAttribute>|Nome do método ou nome da propriedade do chamador.|`String`|

Essas informações ajudam você a escrever rastreamento, depuração e criar ferramentas de diagnóstico. O exemplo a seguir mostra como usar os atributos de informações do chamador. Em cada chamada para o método `TraceMessage`, as informações do chamador são substituídas como argumentos para os parâmetros opcionais.

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

Você especifica um valor padrão explícito para cada parâmetro opcional. Você não pode aplicar atributos de informações de chamadas a parâmetros que não são especificados como opcionais. Os atributos de informações do chamador não tornam um parâmetro opcional. Em vez disso, eles afetam o valor padrão que é passado quando o argumento é omitido. Os valores de informações do chamador são emitidos como literais na Língua Intermediária (IL) no momento da compilação. Ao contrário dos resultados da propriedade <xref:System.Exception.StackTrace%2A> para exceções, os resultados não são afetados por ofuscamento. Você pode fornecer explicitamente os argumentos opcionais para controlar as informações do chamador ou ocultá-las.

### <a name="member-names"></a>Nomes dos membros

Você pode usar o atributo `CallerMemberName` para evitar especificar o nome do membro como um argumento `String` ao método chamado. Ao usar essa técnica, você evita o problema de que a **Refatoração de Renomeação** não altera os valores de `String`. Esse benefício é especialmente útil para as seguintes tarefas:

- Usar rotinas de rastreamento e diagnóstico.
- Implementando a interface <xref:System.ComponentModel.INotifyPropertyChanged> ao associar dados. Essa interface permite que a propriedade de um objeto notifique um controle associado sobre a alteração da propriedade de modo que o controle possa exibir as informações atualizadas. Sem o atributo `CallerMemberName`, você deve especificar o nome da propriedade como um literal.

O gráfico a seguir mostra os nomes de membros que são retornados quando você usa o atributo `CallerMemberName`.

|Chamadas ocorrem dentro|Resultado de nome de membro|
|-|-|
|Método, propriedade ou evento|O nome do método, da propriedade ou do evento em que a chamada foi originada.|
|Construtor|A cadeia de caracteres “.ctor”|
|Construtor estático|A cadeia de caracteres “.cctor”|
|Destruidor|A cadeia de caracteres "Finalize"|
|Operadores usuário ou conversões definidos pelo usuário|O nome gerado para o membro, por exemplo, “op_Addition”.|
|Construtor de atributos|O nome do método ou propriedade ao qual o atributo se aplica. Se o atributo é qualquer elemento dentro de um membro (como um parâmetro, um valor de retorno, ou um parâmetro de tipo genérico), esse resultado é o nome do membro associado a esse elemento.|
|Nenhum membro contentor (por exemplo, nível de assembly ou atributos que são aplicadas aos tipos)|O valor padrão do parâmetro opcional.|

## <a name="see-also"></a>Confira também

- [Argumentos nomeados e opcionais](../../programming-guide/classes-and-structs/named-and-optional-arguments.md)
- <xref:System.Reflection>
- <xref:System.Attribute>
- [Atributos](../../../standard/attributes/index.md)
