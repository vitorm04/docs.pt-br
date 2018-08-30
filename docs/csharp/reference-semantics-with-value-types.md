---
title: Semântica de referência com tipos de valores
description: Compreenda os recursos de linguagem que minimizam, com segurança, a cópia de estruturas
ms.date: 11/10/2017
ms.custom: mvc
ms.openlocfilehash: f241219994d7a03192a4aea69b912bf1ac5ed29c
ms.sourcegitcommit: e614e0f3b031293e4107f37f752be43652f3f253
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/26/2018
ms.locfileid: "42930643"
---
# <a name="reference-semantics-with-value-types"></a>Semântica de referência com tipos de valores

Uma vantagem de usar os tipos de valor é que eles normalmente evitam alocações de heap.
A desvantagem é que eles são copiados por valor. Essa compensação dificulta a otimização de algoritmos que operam em grandes quantidades de dados. Os novos recursos de linguagem em C# 7.2 fornecem mecanismos que habilitam a semântica de transmissão por referência com tipos de valor. Use esses recursos criteriosamente para minimizar tanto as alocações quanto as operações de cópia. Este artigo explora esses novos recursos.

Grande parte do código de exemplo neste artigo demonstra os recursos adicionados em C# 7.2. Para usar esses recursos, você deve configurar seu projeto para usar o C# 7.2 ou posterior. Para obter mais informações sobre como definir a versão da linguagem, confira [Configurar a versão da linguagem](language-reference/configure-language-version.md).

## <a name="passing-arguments-by-readonly-reference"></a>Passando argumentos por referência readonly

O C# 7.2 adiciona a palavra-chave `in` para complementar as palavras-chave `ref` e `out` existente a fim de passar argumentos por referência. A palavra-chave `in` especifica ao passar o argumento por referência, mas o método chamado não modifica o valor. 

Essa adição fornece um vocabulário completo para expressar sua intenção de design. Os tipos de valor são copiados no momento em que são passados para um método chamado quando você não especifica nenhum dos modificadores a seguir na assinatura do método. Cada um desses modificadores especifica que um tipo de valor é transmitido por referência, evitando a cópia. Cada modificador expressa uma intenção diferente:

- `out`: esse método define o valor do argumento usado como este parâmetro.
- `ref`: esse método pode definir o valor do argumento usado como este parâmetro.
- `in`: esse método não modifica o valor do argumento usado como este parâmetro.

Adicione o modificador `in` para passar um argumento por referência e declare que sua intenção de design é passar argumentos por referência para evitar cópias desnecessárias. Você não pretende modificar o objeto utilizado como aquele argumento. O código a seguir mostra um exemplo de um método que calcula a distância entre dois pontos no espaço 3D. 

[!code-csharp[InArgument](../../samples/csharp/reference-semantics/Program.cs#InArgument "Specifying an In argument")]

Os argumentos são duas estruturas que contêm três duplas. Uma dupla tem 8 bytes. Então, cada argumento tem 24 bytes. Ao especificar o modificador `in`, você passa uma referência de 4 ou 8 bytes para esses argumentos, dependendo da arquitetura do computador. A diferença no tamanho é pequena, mas ela pode aumentar rapidamente quando o aplicativo chama esse método em um loop estreito, usando muitos valores diferentes.
 
O modificador `in` complementa `out` e `ref` de outras formas também. Não é possível criar sobrecargas de um método que diferem somente na presença de `in`, `out` ou `ref`. Essas novas regras apresentam o mesmo comportamento que sempre foi definido para os parâmetros `out` e `ref`.

O modificador `in` pode ser aplicado a qualquer membro que usa os seguintes parâmetros: métodos, delegados, lambdas, funções locais, indexadores e operadores.

Ao contrário dos argumentos `ref` e `out`, você pode usar valores literais ou constantes para o argumento em um parâmetro `in`. Além disso, ao contrário de um parâmetro `ref` ou `out`, você não precisa aplicar o modificador `in` no local da chamada. O código a seguir mostra dois exemplos para chamar o método `CalculateDistance`. O primeiro usa duas variáveis locais transmitidas por referência. O segundo inclui uma variável temporária criada como parte da chamada de método. 

[!code-csharp[UseInArgument](../../samples/csharp/reference-semantics/Program.cs#UseInArgument "Specifying an In argument")]

Há várias maneiras pelas quais o compilador garante que a natureza somente leitura de um argumento `in` será aplicada.  Em primeiro lugar, o método chamado não pode ser atribuído diretamente a um parâmetro `in`. Não é possível atribuí-lo diretamente a nenhum campo de um parâmetro `in` quando esse valor é um tipo `struct`. Além disso, você não pode passar um parâmetro `in` para nenhum método usando o modificador `ref` ou `out`.
Essas regras se aplicam a qualquer campo de um parâmetro `in`, considerando que o campo seja um tipo `struct` e o parâmetro também seja um tipo `struct`. Na verdade, essas regras são aplicadas a várias camadas de acesso de membro, considerando que os tipos, em todos os níveis de acesso de membro, sejam `structs`. O compilador impõe que os tipos `struct` passados como argumentos `in` e seus membros `struct` sejam variáveis somente leitura quando usados como argumentos para outros métodos.

O uso de parâmetros `in` evita os possíveis custos de desempenho com a realização de cópias. Isso não altera a semântica de nenhuma chamada de método. Portanto, você não precisa especificar o modificador `in` no site de chamada. No entanto, a omissão do modificador `in` no site de chamada informa ao compilador que ele tem permissão para fazer uma cópia do argumento pelos seguintes motivos:

- Há uma conversão implícita, mas não uma conversão de identidade do tipo de argumento para o tipo de parâmetro.
- O argumento é uma expressão, mas não tem uma variável de armazenamento conhecida.
- Há uma sobrecarga que é distinguível pela presença ou ausência de `in`. Nesse caso, a sobrecarga pelo valor é uma correspondência melhor.

Essas regras são úteis conforme você atualiza o código existente para usar argumentos de referência somente leitura. Dentro do método chamado, você pode chamar qualquer método de instância que use parâmetros por valor. Nessas instâncias, uma cópia do parâmetro `in` é criada. Uma vez que o compilador pode criar uma variável temporária para qualquer parâmetro `in`, você também pode especificar valores padrão para qualquer parâmetro `in`. O código a seguir especifica a origem (ponto 0,0) como o valor padrão para o segundo ponto:

[!code-csharp[InArgumentDefault](../../samples/csharp/reference-semantics/Program.cs#InArgumentDefault "Specifying defaults for an in parameter")]

Para forçar o compilador a passar argumentos somente leitura por referência, especifique o modificador `in` nos argumentos no site de chamada, conforme mostrado no código a seguir:

[!code-csharp[UseInArgument](../../samples/csharp/reference-semantics/Program.cs#ExplicitInArgument "Specifying an In argument")]

Esse comportamento facilita a adoção de parâmetros `in` ao longo do tempo nas grandes bases de código em que os ganhos de desempenho são possíveis. Primeiro você adiciona o modificador `in` às assinaturas de método. Em seguida, você adiciona o modificador `in` em sites de chamada e cria tipos `readonly struct` para evitar que o compilador crie cópias de defesa de parâmetros `in` em mais locais.

A designação do parâmetro `in` também pode ser usada com tipos de referência ou valores numéricos. No entanto, os benefícios em ambos os casos serão mínimos, se houver.

## <a name="ref-readonly-returns"></a>Retornos de `ref readonly`

Talvez você queira retornar um tipo de valor por referência, mas impedir o autor da chamada de modificar esse valor. Use o modificador `ref readonly` para expressar essa intenção de design. Ela notifica os leitores que você está retornando uma referência aos dados existentes, mas não está permitindo a modificação. 

O compilador impõe que o autor da chamada não pode modificar a referência. As tentativas de atribuir o valor diretamente geram um erro em tempo de compilação. No entanto, o compilador não pode saber se algum método de membro modifica o estado da estrutura.
Para garantir que o objeto não será modificado, o compilador cria uma cópia e chama as referências de membro usando essa cópia. Todas as modificações são para essa cópia de defesa. 

É provável que a biblioteca que utiliza o `Point3D` normalmente usaria a origem em todo o código. Cada instância cria um novo objeto na pilha. Pode ser vantajoso criar uma constante e retorná-la por referência. Mas, se retornar uma referência ao armazenamento interno, talvez você queira impor que o autor da chamada não poderá modificar o armazenamento referenciado. O código a seguir define uma propriedade somente leitura que retorna um `readonly ref` para um `Point3D` que especifica a origem.

[!code-csharp[OriginReference](../../samples/csharp/reference-semantics/Point3D.cs#OriginReference "Creating a readonly Origin reference")]

É fácil criar uma cópia de um retorno da referência somente leitura: basta atribui-la a uma variável não declarada com o modificador `ref readonly`. O compilador gera um código para copiar o objeto como parte da atribuição. 

Ao atribuir uma variável a um `ref readonly return`, você pode especificar uma variável `ref readonly` ou uma cópia por valor da referência somente leitura:

[!code-csharp[AssignRefReadonly](../../samples/csharp/reference-semantics/Program.cs#AssignRefReadonly "Assigning a ref readonly")]

A primeira atribuição no código anterior faz uma cópia da constante `Origin` e atribui essa cópia. A segunda atribui uma referência. Observe que o modificador `readonly` deve ser parte da declaração da variável. A referência à qual ele se relaciona não pode ser modificada. As tentativas de modificá-la resultam em um erro em tempo de compilação.

## <a name="readonly-struct-type"></a>Tipo `readonly struct`

A aplicação do `ref readonly` para usos de tráfego intenso de um struct pode ser suficiente.
Em outros momentos, talvez você queira criar um struct imutável. Então, você sempre poderá passar pela referência somente leitura. Essa prática remove a cópia de defesa que é feita quando você acessa os métodos de um struct usado como um parâmetro `in`.

Você pode fazer isso criando um tipo `readonly struct`. Você pode adicionar o modificador `readonly` em uma declaração de struct. O compilador impõe que todos os membros de instância do struct são `readonly`; o `struct` deve ser imutável.

Há outras otimizações para um `readonly struct`. Você pode usar o modificador `in` em todos os locais em que um `readonly struct` é um argumento. Além disso, você pode retornar um `readonly struct` como um `ref return` quando estiver devolvendo um objeto cujo tempo de vida se estende para além do escopo do método que retorna o objeto.

Por fim, o compilador gera um código mais eficiente quando você chama membros de um `readonly struct`: a referência `this`, em vez de uma cópia do destinatário, é sempre um parâmetro `in` transmitido por referência para o método de membro. Essa otimização economiza mais cópias quando você usa um `readonly struct`. O `Point3D` é um ótimo candidato para essa alteração. O código a seguir mostra uma estrutura `ReadonlyPoint3D` atualizada:

[!code-csharp[ReadonlyOnlyPoint3D](../../samples/csharp/reference-semantics/Point3D.cs#ReadonlyOnlyPoint3D "Defining an immutable structure")]

## <a name="ref-struct-type"></a>Tipo `ref struct`

Outro recurso de linguagem relacionado é a capacidade de declarar um tipo de valor que deve ser alocado por pilha. Em outras palavras, esses tipos nunca podem ser criados no heap como um membro de outra classe. A principal motivação para esse recurso foi <xref:System.Span%601> e as estruturas relacionadas. O <xref:System.Span%601> pode conter um ponteiro gerenciado como um de seus membros, sendo o outro o comprimento da extensão. Ele é implementado de modo um pouco diferente porque o C# não é compatível com ponteiros para memória gerenciada fora de um contexto sem segurança. Qualquer gravação que altere o ponteiro e o comprimento não é atômica. Isso significa que um <xref:System.Span%601> estaria sujeito a erros fora do intervalo ou a outras violações de segurança do tipo se não fosse restrito a um único registro de ativação. Além disso, colocar um ponteiro gerenciado no heap de GC normalmente ocasiona uma falha no tempo de JIT.

Você pode ter requisitos semelhantes funcionando com a memória criada usando [`stackalloc`](language-reference/keywords/stackalloc.md) ou ao usar a memória das APIs de interoperabilidade. Você pode definir seus próprios tipos `ref struct` para essas necessidades. Neste artigo, você verá exemplos que usam `Span<T>` para manter a simplicidade.

A declaração `ref struct` declara que um struct desse tipo deve estar na pilha. As regras da linguagem garantem o uso seguro desses tipos. Outros tipos declarados como `ref struct` incluem <xref:System.ReadOnlySpan%601>. 

A meta de manter um tipo `ref struct` como uma variável alocada na pilha apresenta várias regras que o compilador aplica para todos os tipos `ref struct`.

- Você não pode encaixotar um `ref struct`. Você não pode atribuir um tipo `ref struct` a uma variável do tipo `object`, `dynamic` ou de qualquer tipo de interface.
- Você não pode declarar um `ref struct` como um membro de uma classe ou de um struct normal.
- Você não pode declarar variáveis locais que são do tipo `ref struct` em métodos assíncronos. Você pode declará-las em métodos síncronos que retornam `Task`, `Task<T>` ou tipos semelhantes à tarefa.
- Você não pode declarar as variáveis locais `ref struct` em iteradores.
- Você não pode capturar as variáveis `ref struct` em expressões lambda ou em funções locais.

Essas restrições garantem que você não use acidentalmente um `ref struct` de maneira que possa promovê-lo para o heap gerenciado.

## <a name="readonly-ref-struct-type"></a>Tipo `readonly ref struct`

A declaração de um struct como `readonly ref` combina os benefícios e as restrições das declarações `ref struct` e `readonly struct`. 

O seguinte exemplo demonstra a declaração de `readonly ref struct`.

```csharp
readonly ref struct ReadOnlyRefPoint2D
{
    public int X { get; }
    public int Y { get; }
    
    public ReadOnlyRefPoint2D(int x, int y) => (X, Y) = (x, y);
}
```

## <a name="conclusions"></a>Conclusões

Esses aprimoramentos para a linguagem C# são projetados para algoritmos de desempenho importantes, nos quais as alocações de memória podem ser fundamentais para alcançar o desempenho necessário. Você pode achar que geralmente não usa esses recursos no código que grava. No entanto, esses aprimoramentos foram adotados em vários locais no .NET Framework. À medida que mais e mais APIs utilizam esses recursos, você verá o desempenho de seus próprios aplicativos melhorar.
