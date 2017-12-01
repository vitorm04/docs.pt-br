---
title: "Semântica de referência com tipos de valor"
description: "Compreender os recursos de idioma que minimiza as estruturas de cópias com segurança"
author: billwagner
ms.author: wiwagn
ms.date: 11/10/2017
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.custom: mvc
ms.openlocfilehash: 9eeaf201c1f5a58044db62e356199b609c4c035a
ms.sourcegitcommit: 7e99f66ef09d2903e22c789c67ff5a10aa953b2f
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/18/2017
---
# <a name="reference-semantics-with-value-types"></a>Semântica de referência com tipos de valor

Uma vantagem de usar tipos de valor é que eles normalmente evitam alocações de heap.
A desvantagem correspondente é que eles são copiados por valor. Essa compensação dificulta a otimizar os algoritmos que operam em grandes quantidades de dados. Novos recursos de linguagem c# 7.2 fornecem mecanismos que permitem a semântica de passagem-por-referência com tipos de valor. Se você usar esses recursos criteriosamente pode minimizar a ambas as alocações e operações de cópia. Este artigo explora esses novos recursos.

Grande parte do código de exemplo neste artigo demonstra os recursos adicionados no c# 7.2. Para usar esses recursos, você precisa configurar seu projeto para usar o c# 7.2 ou posterior em seu projeto. Você pode usar o Visual Studio para selecioná-la. Para cada projeto, selecione **projeto** no menu, em seguida, **propriedades**. Selecione o **criar** guia e clique em **avançado**. A partir daí, você pode configurar a versão de idioma. Escolha "7.2" ou "mais recente".  Ou você pode editar o *csproj* e adicione o seguinte nó:

```XML
  <PropertyGroup>
    <LangVersion>7.2</LangVersion>
  </PropertyGroup>
```

Você pode usar "7.2" ou "mais recente" para o valor.

## <a name="specifying-in-parameters"></a>Especificando `in` parâmetros

7.2 c# adiciona o `in` palavra-chave para complementar existente `ref` e `out` palavras-chave quando você escreve um método que passa os argumentos por referência. O `in` palavra-chave especifica que você está passando o parâmetro por referência e o método chamado não modifica o valor passado para ele. 

Essa adição fornece um vocabulário completo para expressar sua intenção de design. Tipos de valor são copiados quando passados para um método chamado quando você não especificar qualquer um dos seguintes modificadores. Cada um desses modificadores de especificar se um tipo de valor é passado por referência, evitando a cópia. Cada modificador expressa um propósito diferente:

- `out`: Esse método define o valor do argumento usado como esse parâmetro.
- `ref`: Esse método pode definir o valor do argumento usado como esse parâmetro.
- `in`: Esse método não modifica o valor do argumento usado como esse parâmetro.

Quando você adiciona o `in` modificador para passar um argumento por referência, você declarar sua intenção de design é passar argumentos por referência para evitar a cópia desnecessários. Você não pretende modificar o objeto usado como argumento. O código a seguir mostra um exemplo de um método que calcula a distância entre dois pontos no espaço 3D. 

[!code-csharp[InArgument](../../samples/csharp/reference-semantics/Program.cs#InArgument "Specifying an In argument")]

Os argumentos são duas estruturas que contêm três dobras. Um valor double é de 8 bytes, para que cada argumento é de 24 bytes. Especificando o `in` modificador, passar referência de 4 ou 8 bytes para esses argumentos, dependendo da arquitetura do computador. A diferença no tamanho é pequena, mas ela pode adicionar rapidamente quando o aplicativo chama esse método em um loop estreito, usando muitos valores diferentes.
 
O `in` complementa modificador `out` e `ref` de outras formas também. Não é possível criar sobrecargas de um método que diferem somente na presença de `in`, `out` ou `ref`. O mesmo comportamento que sempre tivesse sido definido para estendem a essas novas regras `out` e `ref` parâmetros.

O `in` modificador pode ser aplicado a qualquer membro que usa parâmetros: métodos, delegados, lambdas, funções locais, indexadores, operadores.

Ao contrário de `ref` e `out` argumentos, você pode usar valores literais ou constantes para o argumento para uma `in` parâmetro. Além disso, ao contrário de um `ref` ou `out` parâmetro, você não precisa aplicar o `in` modificador no site de chamada. O código a seguir mostra dois exemplos de chamar o `CalculateDistance` método. O primeiro usa duas variáveis locais, passadas por referência. O segundo inclui uma variável temporária criada como parte da chamada de método. 

[!code-csharp[UseInArgument](../../samples/csharp/reference-semantics/Program.cs#UseInArgument "Specifying an In argument")]

Há várias maneiras em que o compilador garante que, a natureza de somente leitura de um `in` argumento é imposto.  Primeiro, o método chamado não pode atribuir diretamente a um `in` parâmetro. Não é possível atribuir diretamente para qualquer campo de um `in` parâmetro. Além disso, você não pode passar um `in` parâmetro para qualquer método exigindo o `ref` ou `out` modificador.
O compilador impõe que o `in` argumento é uma variável somente leitura. Você pode chamar qualquer método de instância que usa semântica de passagem-por-valor. Nesses casos, uma cópia do `in` parâmetro é criado. Porque o compilador pode criar uma variável temporária para qualquer `in` parâmetro, você também pode especificar valores padrão para qualquer `in` parâmetro. O código a seguir que usa para especificar a origem (0,0 ponto) como o valor padrão para o segundo ponto:

[!code-csharp[InArgumentDefault](../../samples/csharp/reference-semantics/Program.cs#InArgumentDefault "Specifying defaults for an in parameter")]

O `in` designação de parâmetro também pode ser usada com tipos de referência ou criada em valores numéricos. No entanto, os benefícios em ambos os casos são mínimos, se houver.

## <a name="ref-readonly-returns"></a>`ref readonly`Retorna

Talvez você queira retornar um tipo de valor por referência, mas impedir que o chamador de modificar esse valor. Use o `ref readonly` modificador para expressar essa intenção de design. Notifica os leitores que você está retornando uma referência aos dados existentes, mas não permitir a modificação. 

O compilador impõe que o chamador não é possível modificar a referência. Tenta atribuir diretamente para o valor gerado um erro de tempo de compilação. No entanto, o compilador não pode saber se qualquer método de membro modifica o estado da estrutura.
Para garantir que o objeto não é modificado, o compilador cria uma cópia e chama o membro referências usando essa cópia. Todas as modificações são para a cópia defesa. 

É provável que a biblioteca usando `Point3D` normalmente usaria a origem em todo o código. Cada instância cria um novo objeto na pilha. Pode ser vantajoso para criar uma constante e retorná-lo por referência. Mas, se você retornar uma referência ao armazenamento interno, você pode impor que o chamador não é possível modificar o armazenamento referenciado. O código a seguir define uma propriedade somente leitura que retorna um `readonly ref` para um `Point3D` que especifica a origem.

[!code-csharp[OriginReference](../../samples/csharp/reference-semantics/Point3D.cs#OriginReference "Creating a readonly Origin reference")]

É fácil criar uma cópia de uma ref readonly retorno: apenas o atribui a uma variável não declarada com o `ref readonly` modificador. O compilador gera código para copiar o objeto como parte da atribuição. 

Quando você atribui uma variável para um `ref readonly return`, você pode especificar um `ref readonly` variável ou uma cópia por valor da referência somente leitura:

[!code-csharp[AssignRefReadonly](../../samples/csharp/reference-semantics/Program.cs#AssignRefReadonly "Assigning a ref readonly")]

A primeira atribuição no código anterior faz uma cópia do `Origin` constante e atribui a copia. O segundo atribui uma referência. Observe que o `readonly` modificador deve ser parte da declaração da variável. A referência ao qual se refere não pode ser modificada. Tentativas de fazer isso resultar em um erro em tempo de compilação.

## <a name="readonly-struct-type"></a>Tipo `readonly struct`

Aplicando `ref readonly` para usos de alto tráfego de uma estrutura pode ser suficiente.
Outras vezes, você talvez queira criar uma estrutura imutável. Em seguida, você sempre pode passar por referência somente leitura. Prática remove defensiva copia que ocorrem quando você acessa os métodos de uma estrutura usada como um `in` parâmetro.

Você pode fazer isso criando um `readonly struct` tipo. Você pode adicionar o `readonly` modificador para uma declaração de estrutura. O compilador impõe que todos os membros da estrutura são `readonly`; o `struct` deve ser imutável.

Há outras otimizações para um `readonly struct`. Você pode usar o `in` modificador em todos os locais onde um `readonly struct` é um argumento. Além disso, você pode retornar um `readonly struct` como um `ref return` quando você estiver retornando um objeto cujo tempo de vida se estende além do escopo do método que retornar o objeto.

Por fim, o compilador gera o código mais eficiente quando você chamar membros de um `readonly struct`: O `this` referência, em vez de uma cópia do destinatário, é sempre uma `in` parâmetro passado por referência para o método de membro. Essa otimização salva a cópia mais quando você usar um `readonly struct`. O `Point3D` é um ótimo candidato para que essa alteração. O código a seguir mostra um atualizada `ReadonlyPoint3D` estrutura:

[!code-csharp[ReadonlyOnlyPoint3D](../../samples/csharp/reference-semantics/Point3D.cs#ReadonlyOnlyPoint3D "Defining an immutable structure")]

## <a name="ref-struct-type"></a>Tipo `ref struct`

Outro recurso de idioma relacionados é a capacidade de declarar um tipo de valor que deve ser alocada de pilha. Em outras palavras, esses tipos nunca podem ser criados no heap como um membro de outra classe. A principal motivação para esse recurso foi <xref:System.Span%601> e estruturas relacionadas. <xref:System.Span%601>pode conter um ponteiro gerenciado como um de seus membros, o outro sendo o comprimento da extensão. Na verdade, ele é implementado um pouco diferente porque c# não dá suporte a ponteiros para memória gerenciada fora de um contexto sem segurança. Qualquer gravação que altera o ponteiro e o comprimento não é atômica. Isso significa que um <xref:System.Span%601> seria sujeito a erros de intervalo insuficiente ou outras violações de segurança de tipo foram ele não restrito a um único registro de ativação. Além disso, colocar um ponteiro gerenciado no heap de GC normalmente falha no tempo de JIT.

Você pode ter requisitos semelhantes de trabalhar com memória criada usando [ `stackalloc` ](language-reference/keywords/stackalloc.md) ou ao usar a memória de APIs de interoperabilidade. Você pode definir suas próprias `ref struct` tipos para essas necessidades. Neste artigo, você ver exemplos que usam `Span<T>` para manter a simplicidade.

O `ref struct` declaração declara que uma estrutura desse tipo deve ser na pilha. As regras do idioma garantem o uso seguro desses tipos. Outros tipos declarados como `ref struct` incluem <xref:System.ReadOnlySpan%601>. 

O objetivo de manter uma `ref struct` digite como uma variável alocado na pilha apresenta várias regras que o compilador aplica para todos os `ref struct` tipos.

- Não é possível caixa um `ref struct`. Não é possível atribuir um `ref struct` tipo a uma variável do tipo `object`, `dynamic`, ou qualquer tipo de interface.
- Você não pode declarar um `ref struct` como um membro de uma classe ou uma estrutura normal.
- Não é possível declarar variáveis locais que são `ref struct` tipos de métodos assíncronos. Você pode declará-los em métodos síncronos que retornam `Task`, `Task<T>` ou tipos de tarefas.
- Você não pode declarar `ref struct` variáveis locais em iteradores.
- Não é possível capturar `ref struct` variáveis em expressões lambda ou funções locais.

Essas restrições Certifique-se de que você não os use acidentalmente um `ref struct` de forma que pôde promovê-la para o heap gerenciado.

## <a name="conclusions"></a>Conclusões

Esses aprimoramentos para a linguagem c# são projetados para algoritmos críticas de desempenho onde as alocações de memória podem ser fundamentais para alcançar o desempenho necessário. Você pode achar que muitas vezes você não usar esses recursos no código que você escrever. No entanto, esses aprimoramentos foram adotados em vários locais no .NET Framework. Como fazer mais APIs utiliza esses recursos, você verá o desempenho de seus próprios aplicativos melhorar.
