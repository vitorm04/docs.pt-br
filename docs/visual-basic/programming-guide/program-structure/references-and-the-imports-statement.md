---
title: Referências e a instrução Imports
ms.date: 07/20/2015
helpviewer_keywords:
- assemblies [Visual Basic], namespaces
- references [Visual Basic], assembly
- namespaces [Visual Basic], assemblies
- referencing assemblies
- Imports statement [Visual Basic], referencing assemblies
- assemblies [Visual Basic], references
ms.assetid: 38149bd4-0a6f-4b31-b5f8-94a8c33f1600
ms.openlocfilehash: 31b4fe001f2b8a62ac30488053c57cd186020421
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74347275"
---
# <a name="references-and-the-imports-statement-visual-basic"></a>Referências e a instrução Imports (Visual Basic)
Você pode disponibilizar objetos externos para seu projeto escolhendo o comando **Adicionar referência** no menu **projeto** . Referências no Visual Basic podem apontar para assemblies, que são como bibliotecas de tipos, mas contêm mais informações.  
  
## <a name="the-imports-statement"></a>A instrução Imports  
 Os assemblies incluem um ou mais namespaces. Quando você adiciona uma referência a um assembly, também pode adicionar uma instrução `Imports` a um módulo que controla a visibilidade dos namespaces desse assembly dentro do módulo. A instrução `Imports` fornece um contexto de escopo que permite que você use apenas a parte do namespace necessário para fornecer uma referência exclusiva.  
  
 A instrução `Imports` tem a seguinte sintaxe:  
  
 `Imports [Aliasname =] Namespace`  
  
 `Aliasname` se refere a um nome curto que você pode usar no código para se referir a um namespace importado. o `Namespace` é um namespace disponível por meio de uma referência de projeto, por meio de uma definição dentro do projeto, ou por meio de uma instrução `Imports` anterior.  
  
 Um módulo pode conter qualquer número de instruções `Imports`. Eles devem aparecer após qualquer instrução `Option`, se presente, mas antes de qualquer outro código.  
  
> [!NOTE]
> Não confunda referências de projeto com a instrução `Imports` ou a instrução `Declare`. Referências de projeto tornam objetos externos, como objetos em assemblies, disponíveis para projetos Visual Basic. A instrução `Imports` é usada para simplificar o acesso a referências de projeto, mas não fornece acesso a esses objetos. A instrução `Declare` é usada para declarar uma referência a um procedimento externo em uma DLL (biblioteca de vínculo dinâmico).  
  
## <a name="using-aliases-with-the-imports-statement"></a>Usando aliases com a instrução Imports  
 A instrução `Imports` facilita o acesso a métodos de classes, eliminando a necessidade de digitar explicitamente os nomes totalmente qualificados de referências. Os aliases permitem que você atribua um nome mais amigável a apenas uma parte de um namespace. Por exemplo, a sequência de retorno de carro/alimentação de linha que faz com que uma única parte do texto seja exibida em várias linhas faz parte do módulo <xref:Microsoft.VisualBasic.ControlChars> no namespace <xref:Microsoft.VisualBasic?displayProperty=nameWithType>. Para usar essa constante em um programa sem um alias, você precisaria digitar o seguinte código:  
  
 [!code-vb[VbVbalrApplication#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrApplication/VB/Class1.vb#3)]  
  
 `Imports` instruções sempre devem ser as primeiras linhas imediatamente após qualquer instrução de `Option` em um módulo. O fragmento de código a seguir mostra como importar e atribuir um alias ao módulo <xref:Microsoft.VisualBasic.ControlChars?displayProperty=nameWithType>:  
  
 [!code-vb[VbVbalrApplication#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrApplication/VB/Class1.vb#4)]  
  
 Referências futuras para esse namespace podem ser consideravelmente mais curtas:  
  
 [!code-vb[VbVbalrApplication#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrApplication/VB/Class1.vb#5)]  
  
 Se uma instrução `Imports` não incluir um nome de alias, os elementos definidos no namespace importado poderão ser usados no módulo sem qualificação. Se o nome do alias for especificado, ele deverá ser usado como um qualificador para nomes contidos nesse namespace.  
  
## <a name="see-also"></a>Consulte também

- <xref:Microsoft.VisualBasic.ControlChars>
- <xref:Microsoft.VisualBasic>
- [Namespaces no Visual Basic](namespaces.md)
- [Assemblies no .NET](../../../standard/assembly/index.md)
- [Instrução Imports (Tipo e Namespace .NET)](../../language-reference/statements/imports-statement-net-namespace-and-type.md)
