---
title: Informações do chamador (C#)
ms.date: 07/20/2015
ms.assetid: ffad3d24-2fb7-4641-9124-53b5bc91d339
ms.openlocfilehash: 4b2c34945b47db01b0e655f68f92e4dae7445c2c
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69595343"
---
# <a name="caller-information-c"></a>Informações do chamador (C#)

Ao usar atributos de informações do chamador, você pode obter informações sobre o chamador de um método. Você pode obter o caminho do arquivo do código-fonte, o número da linha no código-fonte e o nome do membro do chamador. Essas informações são úteis para fins de rastreamento, depuração e criação de ferramentas de diagnóstico.

Para obter essas informações, você deve usar os atributos que são aplicadas aos parâmetros opcionais, cada qual com um valor padrão. A tabela a seguir lista os atributos de informações do chamador que são definidos no namespace de <xref:System.Runtime.CompilerServices?displayProperty=nameWithType>:

|Atributo|DESCRIÇÃO|Tipo|
|---|---|---|
|<xref:System.Runtime.CompilerServices.CallerFilePathAttribute>|O caminho completo do arquivo de origem que contém o chamador. Esse é o caminho do arquivo no momento da compilação.|`String`|
|<xref:System.Runtime.CompilerServices.CallerLineNumberAttribute>|Número da linha no arquivo fonte no qual o método é chamado.|`Integer`|
|<xref:System.Runtime.CompilerServices.CallerMemberNameAttribute>|Nome do método ou da propriedade do chamador. Consulte [Nomes dos membros](#member-names) mais adiante neste tópico.|`String`|

## <a name="example"></a>Exemplo

O exemplo a seguir mostra como usar os atributos de informações do chamador. Em cada chamada para o método `TraceMessage`, as informações do chamador são substituídas como argumentos para os parâmetros opcionais.

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

## <a name="remarks"></a>Comentários

Você deve especificar um valor padrão explícito para cada parâmetro opcional. Você não pode aplicar atributos de informações do chamador aos parâmetros que não são especificados como opcionais.

Os atributos de informações do chamador não tornam um parâmetro opcional. Em vez disso, eles afetam o valor padrão que é passado quando o argumento é omitido.

Os valores de informações do chamador são emitidos como literais em linguagem intermediária (IL) em tempo de compilação. Ao contrário dos resultados da propriedade <xref:System.Exception.StackTrace%2A> para exceções, os resultados não são afetados por ofuscamento.

Você pode fornecer explicitamente os argumentos opcionais para controlar as informações do chamador ou ocultá-las.

### <a name="member-names"></a>Nomes dos membros

Você pode usar o atributo `CallerMemberName` para evitar especificar o nome do membro como um argumento `String` ao método chamado. Ao usar essa técnica, você evita o problema de que a **Refatoração de Renomeação** não altera os valores de `String`. Esse benefício é especialmente útil para as seguintes tarefas:

- Usar rotinas de rastreamento e diagnóstico.

- Implementando a interface <xref:System.ComponentModel.INotifyPropertyChanged> ao associar dados. Essa interface permite que a propriedade de um objeto notifique um controle associado sobre a alteração da propriedade de modo que o controle possa exibir as informações atualizadas. Sem o atributo `CallerMemberName`, você deve especificar o nome da propriedade como um literal.

O gráfico a seguir mostra os nomes de membros que são retornados quando você usa o atributo `CallerMemberName`.

|As chamadas ocorrem em|Resultado de nome de membro|
|-|-|
|Método, propriedade ou evento|O nome do método, da propriedade ou do evento em que a chamada foi originada.|
|Construtor|A cadeia de caracteres “.ctor”|
|Construtor estático|A cadeia de caracteres “.cctor”|
|Destruidor|A cadeia de caracteres "Finalize"|
|Operadores usuário ou conversões definidos pelo usuário|O nome gerado para o membro, por exemplo, “op_Addition”.|
|Construtor de atributos|O nome do método ou propriedade ao qual o atributo se aplica. Se o atributo é qualquer elemento dentro de um membro (como um parâmetro, um valor de retorno, ou um parâmetro de tipo genérico), esse resultado é o nome do membro associado a esse elemento.|
|Nenhum membro contentor (por exemplo, nível de assembly ou atributos que são aplicadas aos tipos)|O valor padrão do parâmetro opcional.|

## <a name="see-also"></a>Consulte também

- [Atributos (C#)](./attributes/index.md)
- [Atributos comuns (C#)](./attributes/common-attributes.md)
- [Argumentos nomeados e opcionais](../classes-and-structs/named-and-optional-arguments.md)
- [Conceitos de programação (C#)](./index.md)
