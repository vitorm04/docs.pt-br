---
title: Instrução Event (Visual Basic)
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
ms.openlocfilehash: 2f600f3ed37f38ddd7d86300231e0c447f458aa6
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58831885"
---
# <a name="event-statement"></a>Instrução Event
Declara um evento definido pelo usuário.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
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
|`attrlist`|Opcional. Lista de atributos que se aplicam a esse evento. Vários atributos são separados por vírgulas. Você deve colocar o [lista de atributos](../../../visual-basic/language-reference/statements/attribute-list.md) colchetes angulares ("`<`"e"`>`").|  
|`accessmodifier`|Opcional. Especifica qual código pode acessar o evento. Pode ser uma das seguintes opções:<br /><br /> -   [Público](../../../visual-basic/language-reference/modifiers/public.md)— qualquer código que pode acessar o elemento que o declara pode acessá-lo.<br />-   [Protegido](../../../visual-basic/language-reference/modifiers/protected.md)— somente o código dentro de sua classe ou uma classe derivada pode acessá-lo.<br />-   [Friend](../../../visual-basic/language-reference/modifiers/friend.md)— apenas código no mesmo assembly pode acessá-lo.<br />-   [Privada](../../../visual-basic/language-reference/modifiers/private.md)— somente o código no elemento que o declara pode acessá-lo.<br /> -   [Protected Friend](../../language-reference/modifiers/protected-friend.md)-apenas código no mesmo assembly, uma classe derivada ou classe do evento pode acessá-lo. <br />- [Privado protegido](../../language-reference/modifiers/private-protected.md)-somente o código na classe do evento ou uma classe derivada no mesmo assembly pode acessá-lo.|  
|`Shared`|Opcional. Especifica que esse evento não está associado uma instância específica de uma classe ou estrutura.|  
|`Shadows`|Opcional. Indica que este evento redeclara e oculta um elemento de programação com o mesmo nome, ou conjunto de elementos sobrecarregados, em uma classe base. Você pode sombrear qualquer tipo de elemento declarado com qualquer outro tipo.<br /><br /> Um elemento sombreado não está disponível de dentro da classe derivada que sombreia, com exceção de onde o elemento sombreador é inacessível. Por exemplo, se um `Private` elemento sombreia um elemento de classe base, o código que não tem permissão para acessar o `Private` elemento acessa o elemento de classe base em vez disso.|  
|`eventname`|Necessário. Nome do evento; segue as convenções de nomenclatura de variável padrão.|  
|`parameterlist`|Opcional. Lista de variáveis locais que representam os parâmetros desse evento. Você deve colocar o [lista de parâmetros](../../../visual-basic/language-reference/statements/parameter-list.md) entre parênteses.|  
|`Implements`|Opcional. Indica que este evento implementa um evento de uma interface.|  
|`implementslist`|Necessário se `Implements` for fornecido. Lista de `Sub` procedimentos que está sendo implementados. Vários procedimentos são separados por vírgulas:<br /><br /> *implementedprocedure* [ , *implementedprocedure* ... ]<br /><br /> Cada `implementedprocedure` tem a seguinte sintaxe e partes:<br /><br /> `interface`.`definedname`<br /><br /> -   `interface` -Required. Nome de uma interface que este procedimento do que contém a classe ou estrutura está implementando.<br />-   `Definedname` -Required. Nome pelo qual o procedimento é definido em `interface`. Isso não precisa ser o mesmo que `name`, o nome que está usando este procedimento para implementar o procedimento definido.|  
|`Custom`|Necessário. Os eventos declarados como `Custom` deve definir personalizado `AddHandler`, `RemoveHandler`, e `RaiseEvent` acessadores.|  
|`delegatename`|Opcional. O nome de um delegado que especifica a assinatura de manipulador de eventos.|  
|`AddHandler`|Necessário. Declara um `AddHandler` acessador que especifica as instruções para executar quando um manipulador de eventos é adicionado, explicitamente usando o `AddHandler` instrução ou implicitamente, usando o `Handles` cláusula.|  
|`End AddHandler`|Necessário. Encerra o `AddHandler` bloco.|  
|`value`|Necessário. Nome do parâmetro.|  
|`RemoveHandler`|Necessário. Declara um `RemoveHandler` acessador, que especifica as instruções para executar quando um manipulador de eventos é removido usando o `RemoveHandler` instrução.|  
|`End RemoveHandler`|Necessário. Encerra o `RemoveHandler` bloco.|  
|`RaiseEvent`|Necessário. Declara um `RaiseEvent` acessador, que especifica as instruções para executar quando o evento é gerado usando o `RaiseEvent` instrução. Normalmente, isso invoca uma lista dos representantes mantido pela `AddHandler` e `RemoveHandler` acessadores.|  
|`End RaiseEvent`|Necessário. Encerra o `RaiseEvent` bloco.|  
|`delegatesignature`|Necessário. Lista de parâmetros que corresponde aos parâmetros exigidos pelo `delegatename` delegar. Você deve colocar o [lista de parâmetros](../../../visual-basic/language-reference/statements/parameter-list.md) entre parênteses.|  
|`statements`|Opcional. Instruções que contêm o corpo dos `AddHandler`, `RemoveHandler`, e `RaiseEvent` métodos.|  
|`End Event`|Necessário. Encerra o `Event` bloco.|  
  
## <a name="remarks"></a>Comentários  
 Depois que o evento foi declarado, use o `RaiseEvent` instrução para gerar o evento. Um evento típico pode ser declarado e levantado conforme os fragmentos a seguir:  
  
 [!code-vb[VbVbalrEvents#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#13)]  
  
> [!NOTE]
>  Você pode declarar argumentos de evento, assim como faria argumentos dos procedimentos, com as seguintes exceções: eventos não podem ter argumentos, nomeados `ParamArray` argumentos, ou `Optional` argumentos. Eventos não têm valores de retorno.  
  
 Para manipular um evento, você deve associá-lo com uma sub-rotina de manipulador de eventos usando o `Handles` ou `AddHandler` instrução. As assinaturas de sub-rotina e o evento devem corresponder. Para manipular um evento compartilhado, você deve usar o `AddHandler` instrução.  
  
 Você pode usar `Event` apenas no nível de módulo. Isso significa que o *contexto de declaração* para um evento deve ser uma classe, estrutura, módulo ou interface e não pode ser um arquivo de origem, namespace, procedimento ou bloco. Para obter mais informações, consulte [Contextos de declaração e níveis de acesso padrão](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).  
  
 Na maioria das circunstâncias, você pode usar a primeira sintaxe na seção sintaxe deste tópico para declarar eventos. No entanto, alguns cenários exigem que você tenha mais controle sobre o comportamento detalhado do evento. A última sintaxe na seção Sintaxe neste tópico, que usa o `Custom` palavra-chave, fornece esse controle, permitindo que você defina eventos personalizados. Em um evento personalizado, você pode especificar exatamente o que ocorre quando o código adiciona ou remove um manipulador de eventos ou a partir do evento, ou quando o código gera o evento. Para ver mais exemplos, veja [Como: Declarar eventos personalizados para conservar memória](../../../visual-basic/programming-guide/language-features/events/how-to-declare-custom-events-to-conserve-memory.md) e [como: Declarar eventos personalizados para evitar o bloqueio](../../../visual-basic/programming-guide/language-features/events/how-to-declare-custom-events-to-avoid-blocking.md).  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir usa os eventos a contagem regressiva de 10 segundos para 0. O código ilustra vários dos métodos relacionados a eventos, propriedades e instruções. Isso inclui o `RaiseEvent` instrução.  
  
 A classe que gera um evento é a origem do evento e os métodos que processam o evento são os manipuladores de eventos. Uma origem do evento pode ter vários manipuladores para eventos que ela gera. Quando a classe gera o evento, esse evento é gerado em cada classe que decidiu manipular eventos para essa instância do objeto.  
  
 O exemplo também usa um formulário (`Form1`) com um botão (`Button1`) e uma caixa de texto (`TextBox1`). Quando você clica no botão, a primeira caixa de texto exibe uma contagem regressiva de 10 para 0 segundos. Depois de decorrido o tempo total (10 segundos), a primeira caixa de texto exibe "Concluído".  
  
 O código para `Form1` Especifica os estados iniciais e de terminal do formulário. Ele também contém o código executado quando os eventos são gerados.  
  
 Para usar este exemplo, abra um novo projeto Windows Forms. Em seguida, adicione um botão chamado `Button1` e uma caixa de texto denominada `TextBox1` ao formulário principal, chamado `Form1`. Em seguida, clique com botão direito do formulário e clique em **Exibir código** para abrir o editor de código.  
  
 Adicionar um `WithEvents` à seção declarations da variável a `Form1` classe:  
  
 [!code-vb[VbVbalrEvents#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#14)]  
  
 Adicione o seguinte código para o código para `Form1`. Substituir qualquer procedimentos duplicados que podem existir, tal como `Form_Load` ou `Button_Click`.  
  
 [!code-vb[VbVbalrEvents#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#15)]  
  
 Pressione F5 para executar o exemplo anterior e clique no botão rotulado **iniciar**. A primeira caixa de texto começa a contagem regressiva de segundos. Depois de decorrido o tempo total (10 segundos), a primeira caixa de texto exibe "Concluído".  
  
> [!NOTE]
>  O `My.Application.DoEvents` método não processa os eventos da mesma maneira que faz o formulário. Para habilitar o formulário manipular os eventos diretamente, você pode usar multithreading. Para obter mais informações, consulte [Threading gerenciado](../../../standard/threading/index.md).  
  
## <a name="see-also"></a>Consulte também

- [Instrução RaiseEvent](../../../visual-basic/language-reference/statements/raiseevent-statement.md)
- [Instrução Implements](../../../visual-basic/language-reference/statements/implements-statement.md)
- [Eventos](../../../visual-basic/programming-guide/language-features/events/index.md)
- [Instrução AddHandler](../../../visual-basic/language-reference/statements/addhandler-statement.md)
- [Instrução RemoveHandler](../../../visual-basic/language-reference/statements/removehandler-statement.md)
- [Handles](../../../visual-basic/language-reference/statements/handles-clause.md)
- [Instrução Delegate](../../../visual-basic/language-reference/statements/delegate-statement.md)
- [Como: Declarar eventos personalizados para conservar a memória](../../../visual-basic/programming-guide/language-features/events/how-to-declare-custom-events-to-conserve-memory.md)
- [Como: Declarar eventos personalizados para evitar bloqueio](../../../visual-basic/programming-guide/language-features/events/how-to-declare-custom-events-to-avoid-blocking.md)
- [Compartilhado](../../../visual-basic/language-reference/modifiers/shared.md)
- [Sombras](../../../visual-basic/language-reference/modifiers/shadows.md)
