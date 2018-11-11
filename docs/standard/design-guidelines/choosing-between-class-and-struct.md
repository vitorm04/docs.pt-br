---
title: Escolhendo entre a classe e Struct
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- class library design guidelines [.NET Framework], structures
- class library design guidelines [.NET Framework], classes
- structures [.NET Framework], vs. classes
- classes [.NET Framework], design guidelines
- type design guidelines, structures
- structures [.NET Framework], design guidelines
- classes [.NET Framework], vs. structures
- type design guidelines, classes
ms.assetid: f8b8ec9b-0ba7-4dea-aadf-a93395cd804f
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7590d5628f4951a8c7c2199f0e954007ed9fa962
ms.sourcegitcommit: b5cd9d5d3b75a5537fc9ad8a3f085f0bb1845ee0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/07/2018
ms.locfileid: "50757420"
---
# <a name="choosing-between-class-and-struct"></a>Escolhendo entre a classe e Struct
Uma das decisões de design básica que faces cada designer de estrutura é se deseja criar um tipo como uma classe (um tipo de referência) ou como um struct (um tipo de valor). Boa compreensão das diferenças no comportamento dos tipos de referência e tipos de valor é fundamental para fazer essa escolha.  
  
 A primeira diferença entre os tipos de referência e tipos de valor, consideraremos é que tipos de referência são alocados no heap e coleta de lixo, ao passo que tipos de valor são alocados na pilha ou embutido no que contém tipos e desalocada quando a pilha esvazia ou quando seu tipo recipiente é desalocado. Portanto, as alocações e Desalocações de tipos de valor são em geral, mais barato do que as alocações e Desalocações de tipos de referência.  
  
 Em seguida, matrizes de referência de tipos são alocados fora de linha, que significa que a matriz de elementos são referências apenas para as instâncias do tipo de referência que residem no heap. Matrizes de tipo de valor são alocados em linha, que significa que os elementos da matriz são as instâncias reais do tipo de valor. Portanto, as alocações e Desalocações de matrizes de tipo de valor são muito mais baratas do que as alocações e Desalocações de matrizes de tipo de referência. Além disso, na maioria dos casos, as matrizes de tipo de valor apresentam muito melhor localidade de referência.  
  
 A próxima diferença está relacionada ao uso de memória. Tipos de valor obterem box quando convertido em um tipo de referência ou uma das interfaces que elas implementam. Eles obtêm desconvertidos ao converter para o tipo de valor. Como caixas são objetos que são alocados no heap e coleta de lixo, muito com conversão boxing e unboxing pode ter um impacto negativo sobre o heap, o coletor de lixo e, por fim, o desempenho do aplicativo.  Por outro lado, não há tal conversão boxing ocorre como tipos de referência são convertidos. (Para obter mais informações, consulte [conversão Boxing e Unboxing](../../csharp/programming-guide/types/boxing-and-unboxing.md)).
  
 Em seguida, as atribuições de tipo de referência copiar a referência, enquanto as atribuições de tipo de valor copie o valor inteiro. Portanto, as atribuições de tipos de referência grandes são mais baratas do que as atribuições de tipos de valor grande.  
  
 Por fim, os tipos de referência são passados por referência, enquanto que os tipos de valor são passados por valor. As alterações a uma instância de um tipo de referência afetam todas as referências que apontam para a instância. Instâncias do tipo de valor são copiadas quando eles são passados por valor. Quando uma instância de um tipo de valor é alterada, ele certamente não afeta qualquer uma das suas cópias. Como as cópias não são criadas explicitamente pelo usuário, mas são criadas implicitamente quando os argumentos são passados ou retornam os valores são retornados, tipos de valor que podem ser alterados podem ser confusos para muitos usuários. Portanto, os tipos de valor devem ser imutáveis.  
  
 Como regra geral, a maioria dos tipos em uma estrutura deve ser classes. No entanto, há algumas situações em que as características de um tipo de valor torná-lo mais apropriado usar structs.  
  
 **✓ CONSIDER** definindo um struct, em vez de uma classe, se as instâncias do tipo são pequena e geralmente curta duração ou geralmente são inseridas em outros objetos.  
  
 **X AVOID** definindo uma estrutura, a menos que o tipo tem todas as seguintes características:  
  
-   Logicamente, ele representa um único valor, semelhante aos tipos primitivos (`int`, `double`, etc.).  
  
-   Ele tem um tamanho de instância em 16 bytes.  
  
-   É imutável.  
  
-   Ele não terá a ser demarcado com frequência.  
  
 Em todos os outros casos, você deve definir seus tipos como classes.  
  
 *Portions © 2005, 2009 Microsoft Corporation. Todos os direitos reservados.*  
  
 *Reimpresso com permissão da Pearson Education, Inc. das [Diretrizes de Design do Framework: convenções, linguagens e padrões para bibliotecas do .NET reutilizável, 2ª edição](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) por Krzysztof Cwalina e Brad Abrams, publicado em 22 de outubro de 2008 por Addison-Wesley Professional como parte da série de desenvolvimento do Microsoft Windows.*  
  
## <a name="see-also"></a>Consulte também

- [Diretrizes de Design de tipo](../../../docs/standard/design-guidelines/type.md)  
- [Diretrizes de design do Framework](../../../docs/standard/design-guidelines/index.md)
