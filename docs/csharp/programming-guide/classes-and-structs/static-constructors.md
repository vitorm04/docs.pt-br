---
title: Construtores estáticos – Guia de Programação em C#
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- static constructors [C#]
- constructors [C#], static
ms.assetid: 151ec95e-3c4d-4ed7-885d-95b7a3be2e7d
ms.openlocfilehash: 6d1a39008ebb965649104c2e74241780731911bb
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69596037"
---
# <a name="static-constructors-c-programming-guide"></a>Construtores estáticos (Guia de Programação em C#)
Um construtor estático é usado para inicializar quaisquer dados [estáticos](../../language-reference/keywords/static.md) ou para executar uma ação específica que precisa ser executada apenas uma vez. Ele é chamado automaticamente antes que a primeira instância seja criada ou que quaisquer membros estáticos sejam referenciados.  
  
 [!code-csharp[csProgGuideObjects#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#14)]  
 
## <a name="remarks"></a>Comentários
Construtores estáticos têm as seguintes propriedades:  
  
- Um construtor estático não usa modificadores de acesso nem tem parâmetros.  

- Uma classe ou struct só pode ter um construtor estático.

- Os construtores estáticos não podem ser herdados ou sobrecarregados.

- Um construtor estático não pode ser chamado diretamente e destina-se apenas a ser chamado pela Common Language Runtime (CLR). Ele é invocado automaticamente.

- O usuário não tem controle sobre quando o construtor estático é executado no programa.
  
- Um construtor estático é chamado automaticamente para inicializar a [classe](../../language-reference/keywords/class.md) antes que a primeira instância seja criada ou que quaisquer membros estáticos sejam referenciados. Um construtor estático será executado antes de um construtor de instância. Observe que um construtor de tipo estático é chamado quando um método estático atribuído a um evento ou um delegado é invocado, e não quando ele é atribuído. Se os inicializadores de variável de campo estático estiverem presentes na classe do construtor estático, eles serão executados na ordem textual na qual eles aparecem na declaração de classe imediatamente antes da execução do construtor estático.

- Se você não fornecer um construtor estático para inicializar campos estáticos, todos os campos estáticos serão inicializados com seu valor padrão, conforme listado na [Tabela de Valores Padrão](../../language-reference/keywords/default-values-table.md). 
  
- Se um construtor estático gera uma exceção, o tempo de execução não o invocará uma segunda vez e o tipo permanecerá não inicializado durante o tempo de vida do domínio do aplicativo no qual o programa está sendo executado. Normalmente, uma exceção <xref:System.TypeInitializationException> é lançada quando um construtor estático não consegue instanciar um tipo ou uma exceção sem tratamento que ocorre em um construtor estático. Para construtores estáticos implícitos que não são definidos explicitamente no código-fonte, a solução de problemas pode exigir inspeção do código de linguagem intermediária (IL).

- A presença de um construtor estático impede a adição do atributo do tipo <xref:System.Reflection.TypeAttributes.BeforeFieldInit>. Isso limita a otimização do tempo de execução.

- Um campo declarado como `static readonly` só pode ser atribuído como parte de sua declaração ou em um construtor estático. Quando um construtor estático explícito não for necessário, inicialize os campos estáticos na declaração, em vez de usar um construtor estático para melhorar a otimização do tempo de execução.

> [!Note]
> Embora não seja diretamente acessível, a presença de um construtor estático explícito deve ser documentada para auxiliar na solução de problemas de exceções de inicialização.

### <a name="usage"></a>Uso

- Um uso típico de construtores estáticos é quando a classe está usando um arquivo de log e o construtor é usado para gravar entradas nesse arquivo.  
- Construtores estáticos também são úteis ao criar classes wrapper para código não gerenciado quando o construtor pode chamar o método `LoadLibrary`.  

- Os construtores estáticos também são um local conveniente para impor verificações em tempo de execução no parâmetro de tipo que não pode ser verificado em tempo de compilação por meio de restrições (restrições de parâmetro de tipo).

## <a name="example"></a>Exemplo
 Nesse exemplo, a classe `Bus` tem um construtor estático. Quando a primeira instância do `Bus` for criada (`bus1`), o construtor estático será invocado para inicializar a classe. O exemplo de saída verifica se o construtor estático é executado somente uma vez, mesmo se duas instâncias de `Bus` forem criadas e se é executado antes que o construtor da instância seja executado.  
  
 [!code-csharp[csProgGuideObjects#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#15)]
 
## <a name="c-language-specification"></a>Especificação da linguagem C#
Para saber mais, confira a seção [Construtores estáticos](~/_csharplang/spec/classes.md#static-constructors) da [Especificação da linguagem C#](~/_csharplang/spec/introduction.md).
  
## <a name="see-also"></a>Consulte também

- [Guia de Programação em C#](../index.md)
- [Classes e Structs](./index.md)
- [Construtores](./constructors.md)
- [Classes static e membros de classes static](./static-classes-and-static-class-members.md)
- [Finalizadores](./destructors.md)
- [Diretrizes de design de construtor](../../../standard/design-guidelines/constructor.md#type-constructor-guidelines)
- [Aviso de segurança - CA2121: Construtores estáticos devem ser particulares](https://docs.microsoft.com/visualstudio/code-quality/ca2121-static-constructors-should-be-private)
