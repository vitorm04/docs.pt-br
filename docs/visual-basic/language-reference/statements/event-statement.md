---
title: Instrução de evento (Visual Basic)
ms.date: 05/12/2018
f1_keywords:
- vb.Event
- vb.Custom
helpviewer_keywords:
- Event statement [Visual Basic]
- declaring events [Visual Basic], syntax
- Public keyword [Visual Basic], Event statements
- Custom keyword [Visual Basic]
- declarations [Visual Basic], events
- event keyword [Visual Basic]
- WithEvents keyword [Visual Basic], Event statements
- events [Visual Basic], declaring
- ByVal keyword [Visual Basic], Event statements
- events [Visual Basic], custom
- ByRef keyword [Visual Basic], Event statements
- declaring user-defined events
ms.assetid: 306ff8ed-74dd-4b6a-bd2f-e91b17474042
ms.openlocfilehash: ab4ff31cbc7b16e1d0ad8defed18e523c237e10d
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72583363"
---
# <a name="event-statement"></a>Instrução Event
Declara um evento definido pelo usuário.  
  
## <a name="syntax"></a>Sintaxe  
  
```vb  
[ <attrlist> ] [ accessmodifier ] _  
[ Shared ] [ Shadows ] Event eventname[(parameterlist)] _  
[ Implements implementslist ]  
' -or-  
[ <attrlist> ] [ accessmodifier ] _  
[ Shared ] [ Shadows ] Event eventname As delegatename _  
[ Implements implementslist ]  
' -or-  
 [ <attrlist> ] [ accessmodifier ] _  
[ Shared ] [ Shadows ] Custom Event eventname As delegatename _  
[ Implements implementslist ]  
   [ <attrlist> ] AddHandler(ByVal value As delegatename)  
      [ statements ]  
   End AddHandler  
   [ <attrlist> ] RemoveHandler(ByVal value As delegatename)  
      [ statements ]  
   End RemoveHandler  
   [ <attrlist> ] RaiseEvent(delegatesignature)  
      [ statements ]  
   End RaiseEvent  
End Event  
```  
  
## <a name="parts"></a>Partes  
  
|Parte|Descrição|  
|---|---|  
|`attrlist`|Opcional. Lista de atributos que se aplicam a este evento. Vários atributos são separados por vírgulas. Você deve colocar a [lista de atributos](../../../visual-basic/language-reference/statements/attribute-list.md) entre colchetes angulares ("`<`" e "`>`").|  
|`accessmodifier`|Opcional. Especifica qual código pode acessar o evento. Pode ser um dos seguintes:<br /><br /> -   [público](../../../visual-basic/language-reference/modifiers/public.md)— qualquer código que possa acessar o elemento que o declara pode acessá-lo.<br />-   [protegido](../../../visual-basic/language-reference/modifiers/protected.md)— somente o código dentro de sua classe ou de uma classe derivada pode acessá-lo.<br />-   [Friend](../../../visual-basic/language-reference/modifiers/friend.md)— somente o código no mesmo assembly pode acessá-lo.<br />-   [privado](../../../visual-basic/language-reference/modifiers/private.md)— somente o código no elemento que o declara pode acessá-lo.<br /> -    código somente Friend-only[protegido](../../language-reference/modifiers/protected-friend.md)na classe do evento, uma classe derivada ou o mesmo assembly pode acessá-lo. <br />-  código somente[protegido privado](../../language-reference/modifiers/private-protected.md)na classe do evento ou em uma classe derivada no mesmo assembly pode acessá-lo.|  
|`Shared`|Opcional. Especifica que esse evento não está associado a uma instância específica de uma classe ou estrutura.|  
|`Shadows`|Opcional. Indica que esse evento redeclara e oculta um elemento de programação de nome idêntico, ou conjunto de elementos sobrecarregados, em uma classe base. Você pode sombrear qualquer tipo de elemento declarado com qualquer outro tipo.<br /><br /> Um elemento sombreado não está disponível de dentro da classe derivada que o sombreia, exceto de onde o elemento de sombreamento está inacessível. Por exemplo, se um elemento `Private` sombreia um elemento de classe base, o código que não tem permissão para acessar o elemento `Private` acessa o elemento de classe base em vez disso.|  
|`eventname`|Necessário. Nome do evento; segue as convenções padrão de nomenclatura de variável.|  
|`parameterlist`|Opcional. Lista de variáveis locais que representam os parâmetros deste evento. Você deve colocar a [lista de parâmetros](../../../visual-basic/language-reference/statements/parameter-list.md) entre parênteses.|  
|`Implements`|Opcional. Indica que esse evento implementa um evento de uma interface.|  
|`implementslist`|Necessário se `Implements` for fornecido. Lista de procedimentos de `Sub` que estão sendo implementados. Vários procedimentos são separados por vírgulas:<br /><br /> *implementedprocedure* [, *implementedprocedure* ...]<br /><br /> Cada `implementedprocedure` tem a seguinte sintaxe e partes:<br /><br /> `interface`.`definedname`<br /><br /> -    `interface`-obrigatório. Nome de uma interface que o procedimento que contém a classe ou a estrutura está implementando.<br />-    `Definedname`-obrigatório. Nome pelo qual o procedimento é definido em `interface`. Isso não precisa ser o mesmo que `name`, o nome que este procedimento está usando para implementar o procedimento definido.|  
|`Custom`|Necessário. Eventos declarados como `Custom` devem definir acessadores `AddHandler`, `RemoveHandler` e `RaiseEvent` personalizados.|  
|`delegatename`|Opcional. O nome de um delegado que especifica a assinatura do manipulador de eventos.|  
|`AddHandler`|Necessário. Declara um acessador de `AddHandler`, que especifica as instruções a serem executadas quando um manipulador de eventos é adicionado, seja explicitamente usando a instrução `AddHandler` ou implicitamente usando a cláusula `Handles`.|  
|`End AddHandler`|Necessário. Encerra o bloco de `AddHandler`.|  
|`value`|Necessário. Nome do parâmetro.|  
|`RemoveHandler`|Necessário. Declara um acessador `RemoveHandler`, que especifica as instruções a serem executadas quando um manipulador de eventos é removido usando a instrução `RemoveHandler`.|  
|`End RemoveHandler`|Necessário. Encerra o bloco de `RemoveHandler`.|  
|`RaiseEvent`|Necessário. Declara um acessador `RaiseEvent`, que especifica as instruções a serem executadas quando o evento é gerado usando a instrução `RaiseEvent`. Normalmente, isso invoca uma lista de delegados mantidos pelo `AddHandler` e `RemoveHandler` acessadores.|  
|`End RaiseEvent`|Necessário. Encerra o bloco de `RaiseEvent`.|  
|`delegatesignature`|Necessário. Lista de parâmetros que corresponde aos parâmetros exigidos pelo `delegatename` delegado. Você deve colocar a [lista de parâmetros](../../../visual-basic/language-reference/statements/parameter-list.md) entre parênteses.|  
|`statements`|Opcional. Instruções que contêm os corpos dos métodos `AddHandler`, `RemoveHandler` e `RaiseEvent`.|  
|`End Event`|Necessário. Encerra o bloco de `Event`.|  
  
## <a name="remarks"></a>Comentários  
 Depois que o evento tiver sido declarado, use a instrução `RaiseEvent` para gerar o evento. Um evento típico pode ser declarado e gerado conforme mostrado nos seguintes fragmentos:  
  
 [!code-vb[VbVbalrEvents#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#13)]  
  
> [!NOTE]
> Você pode declarar argumentos de evento da mesma forma como faz argumentos de procedimentos, com as seguintes exceções: eventos não podem ter argumentos nomeados, argumentos de `ParamArray` ou argumentos de `Optional`. Os eventos não têm valores de retorno.  
  
 Para lidar com um evento, você deve associá-lo a uma sub-rotina do manipulador de eventos usando a instrução `Handles` ou `AddHandler`. As assinaturas da sub-rotina e do evento devem corresponder. Para manipular um evento compartilhado, você deve usar a instrução `AddHandler`.  
  
 Você pode usar `Event` somente no nível do módulo. Isso significa que o *contexto de declaração* para um evento deve ser uma classe, estrutura, módulo ou interface e não pode ser um arquivo de origem, namespace, procedimento ou bloco. Para obter mais informações, consulte [Contextos de declaração e níveis de acesso padrão](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).  
  
 Na maioria das circunstâncias, você pode usar a primeira sintaxe na seção sintaxe deste tópico para declarar eventos. No entanto, alguns cenários exigem que você tenha mais controle sobre o comportamento detalhado do evento. A última sintaxe na seção sintaxe deste tópico, que usa a palavra-chave `Custom`, fornece esse controle permitindo que você defina eventos personalizados. Em um evento personalizado, você especifica exatamente o que ocorre quando o código adiciona ou remove um manipulador de eventos de ou para o evento ou quando o código gera o evento. Para obter exemplos, consulte [como: declarar eventos personalizados para conservar memória](../../../visual-basic/programming-guide/language-features/events/how-to-declare-custom-events-to-conserve-memory.md) e [como declarar eventos personalizados para evitar o bloqueio](../../../visual-basic/programming-guide/language-features/events/how-to-declare-custom-events-to-avoid-blocking.md).  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir usa eventos para contar os segundos de 10 a 0. O código ilustra vários dos métodos, propriedades e instruções relacionados ao evento. Isso inclui a instrução `RaiseEvent`.  
  
 A classe que gera um evento é a origem do evento, e os métodos que processam o evento são os manipuladores de eventos. Uma origem de evento pode ter vários manipuladores para os eventos que ele gera. Quando a classe gera o evento, esse evento é gerado em todas as classes que escolheram manipular eventos para essa instância do objeto.  
  
 O exemplo também usa um formulário (`Form1`) com um botão (`Button1`) e uma caixa de texto (`TextBox1`). Quando você clica no botão, a primeira caixa de texto exibe uma contagem regressiva de 10 a 0 segundos. Quando o tempo total (10 segundos) tiver decorrido, a primeira caixa de texto exibirá "concluído".  
  
 O código para `Form1` especifica os Estados inicial e de terminal do formulário. Ele também contém o código executado quando eventos são gerados.  
  
 Para usar este exemplo, abra um novo projeto Windows Forms. Em seguida, adicione um botão chamado `Button1` e uma caixa de texto chamada `TextBox1` ao formulário principal, chamado `Form1`. Em seguida, clique com o botão direito do mouse no formulário e clique em **Exibir código** para abrir o editor de código.  
  
 Adicione uma variável `WithEvents` à seção declarações da classe `Form1`:  
  
 [!code-vb[VbVbalrEvents#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#14)]  
  
 Adicione o código a seguir ao código para `Form1`. Substitua quaisquer procedimentos duplicados que possam existir, como `Form_Load` ou `Button_Click`.  
  
 [!code-vb[VbVbalrEvents#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#15)]  
  
 Pressione F5 para executar o exemplo anterior e clique no botão chamado **Iniciar**. A primeira caixa de texto começa a contar os segundos. Quando o tempo total (10 segundos) tiver decorrido, a primeira caixa de texto exibirá "concluído".  
  
> [!NOTE]
> O método `My.Application.DoEvents` não processa eventos da mesma maneira que o formulário. Para permitir que o formulário manipule os eventos diretamente, você pode usar multithreading. Para obter mais informações, consulte [Threading gerenciado](../../../standard/threading/index.md).  
  
## <a name="see-also"></a>Consulte também

- [Instrução RaiseEvent](../../../visual-basic/language-reference/statements/raiseevent-statement.md)
- [Instrução Implements](../../../visual-basic/language-reference/statements/implements-statement.md)
- [Eventos](../../../visual-basic/programming-guide/language-features/events/index.md)
- [Instrução AddHandler](../../../visual-basic/language-reference/statements/addhandler-statement.md)
- [Instrução RemoveHandler](../../../visual-basic/language-reference/statements/removehandler-statement.md)
- [Handles](../../../visual-basic/language-reference/statements/handles-clause.md)
- [Instrução Delegate](../../../visual-basic/language-reference/statements/delegate-statement.md)
- [Como declarar eventos personalizados para conservar memória](../../../visual-basic/programming-guide/language-features/events/how-to-declare-custom-events-to-conserve-memory.md)
- [Como declarar eventos personalizados para evitar bloqueio](../../../visual-basic/programming-guide/language-features/events/how-to-declare-custom-events-to-avoid-blocking.md)
- [Compartilhado](../../../visual-basic/language-reference/modifiers/shared.md)
- [Sombras](../../../visual-basic/language-reference/modifiers/shadows.md)
