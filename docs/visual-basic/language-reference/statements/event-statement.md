---
title: "Instrução Event | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Event
- vb.Custom
dev_langs:
- VB
helpviewer_keywords:
- Event statement
- declaring events, syntax
- Public keyword, Event statements
- Custom keyword
- declarations, events
- event keyword [Visual Basic]
- WithEvents keyword, Event statements
- events [Visual Basic], declaring
- ByVal keyword, Event statements
- events [Visual Basic], custom
- ByRef keyword, Event statements
- declaring user-defined events
ms.assetid: 306ff8ed-74dd-4b6a-bd2f-e91b17474042
caps.latest.revision: 33
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: b0ea8074f996622df3cd88a7e87fc1156b63dcaf
ms.lasthandoff: 03/13/2017

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
|`attrlist`|Opcional. Lista de atributos que se aplicam a esse evento. Vários atributos são separados por vírgulas. Você deve colocar o [a lista de atributos](../../../visual-basic/language-reference/statements/attribute-list.md) entre colchetes angulares ("`<`"e"`>`").|  
|`accessmodifier`|Opcional. Especifica qual código pode acessar o evento. Pode ser uma das seguintes opções:<br /><br /> -   [Público](../../../visual-basic/language-reference/modifiers/public.md)— qualquer código que pode acessar o elemento que o declara pode acessá-lo.<br />-   [Protegido](../../../visual-basic/language-reference/modifiers/protected.md)— apenas código dentro de sua classe ou uma classe derivada pode acessá-lo.<br />-   [Amigo](../../../visual-basic/language-reference/modifiers/friend.md)— apenas código no mesmo conjunto pode acessá-lo.<br />-   [Privada](../../../visual-basic/language-reference/modifiers/private.md)— apenas código no mesmo elemento que o declara pode acessá-lo.<br /><br /> Você pode especificar `Protected Friend` para habilitar o acesso do código de classe do evento, uma classe derivada ou o mesmo assembly.|  
|`Shared`|Opcional. Especifica que este evento não está associado uma instância específica de uma classe ou estrutura.|  
|`Shadows`|Opcional. Indica que este evento redeclara e oculta um elemento de programação de nome idêntico, ou conjunto de elementos sobrecarregados, na classe base. Você pode sombrear qualquer tipo de elemento declarado com qualquer outro tipo.<br /><br /> Um elemento sombreado não está disponível de dentro da classe derivada que o sombreia, com exceção de onde o elemento sombreamento é inacessível. Por exemplo, se um `Private` elemento sombreia um elemento de classe base, o código que não tem permissão para acessar o `Private` elemento acessa o elemento da classe base em vez disso.|  
|`eventname`|Necessário. Nome do evento; segue as convenções de nomenclatura de variável padrão.|  
|`parameterlist`|Opcional. Lista de variáveis locais que representam os parâmetros desse evento. Você deve colocar o [lista de parâmetros](../../../visual-basic/language-reference/statements/parameter-list.md) entre parênteses.|  
|`Implements`|Opcional. Indica que este evento implementa um evento de uma interface.|  
|`implementslist`|Necessário se `Implements` for fornecido. Lista de `Sub` procedimentos que estão sendo implementados. Vários procedimentos são separados por vírgulas:<br /><br /> *implementedprocedure* [, *implementedprocedure* ...]<br /><br /> Cada `implementedprocedure` tem a seguinte sintaxe e partes:<br /><br /> `interface`.`definedname`<br /><br /> -   `interface`-Necessário. Nome de uma interface que esse procedimento contendo classe ou estrutura está implementando.<br />-   `Definedname`-Necessário. Nome pelo qual o procedimento é definido em `interface`. Isso não precisa ser o mesmo que `name`, o nome que está usando este procedimento para implementar o procedimento definido.|  
|`Custom`|Necessário. Eventos declarados como `Custom` deve definir personalizado `AddHandler`, `RemoveHandler`, e `RaiseEvent` acessadores.|  
|`delegatename`|Opcional. O nome de um delegado que especifica a assinatura do manipulador de eventos.|  
|`AddHandler`|Necessário. Declara um `AddHandler` acessador, que especifica as instruções para executar quando um manipulador de eventos é adicionado, explicitamente usando o `AddHandler` instrução ou implicitamente, usando o `Handles` cláusula.|  
|`End AddHandler`|Necessário. Encerra o `AddHandler` bloco.|  
|`value`|Necessário. Nome do parâmetro.|  
|`RemoveHandler`|Necessário. Declara um `RemoveHandler` acessador, que especifica as instruções para executar quando um manipulador de eventos é removido usando o `RemoveHandler` instrução.|  
|`End RemoveHandler`|Necessário. Encerra o `RemoveHandler` bloco.|  
|`RaiseEvent`|Necessário. Declara um `RaiseEvent` acessador, que especifica as instruções para executar quando o evento é gerado usando o `RaiseEvent` instrução. Normalmente, isso invoca uma lista dos representantes mantido pelo `AddHandler` e `RemoveHandler` acessadores.|  
|`End RaiseEvent`|Necessário. Encerra o `RaiseEvent` bloco.|  
|`delegatesignature`|Necessário. Lista de parâmetros que corresponde aos parâmetros exigidos pelo `delegatename` delegar. Você deve colocar o [lista de parâmetros](../../../visual-basic/language-reference/statements/parameter-list.md) entre parênteses.|  
|`statements`|Opcional. Instruções que contêm o corpo do `AddHandler`, `RemoveHandler`, e `RaiseEvent` métodos.|  
|`End Event`|Necessário. Encerra o `Event` bloco.|  
  
## <a name="remarks"></a>Comentários  
 Depois que o evento foi declarado, use o `RaiseEvent` instrução para gerar o evento. Um evento típico pode ser declarado e levantado conforme os seguintes fragmentos:  
  
 [!code-vb[VbVbalrEvents&13;](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/event-statement_1.vb)]  
  
> [!NOTE]
>  Você pode declarar argumentos de evento, assim como você faz argumentos de procedimentos, com as seguintes exceções: eventos não podem ter argumentos nomeados, `ParamArray` argumentos, ou `Optional` argumentos. Eventos não têm valores de retorno.  
  
 Para manipular um evento, você deve associá-lo com um manipulador de eventos sub-rotina usando o `Handles` ou `AddHandler` instrução. As assinaturas de sub-rotina e o evento devem corresponder. Para manipular um evento compartilhado, você deve usar o `AddHandler` instrução.  
  
 Você pode usar `Event` somente no nível de módulo. Isso significa que o *contexto declaração* para um evento deve ser uma classe, estrutura, módulo ou interface e não pode ser um arquivo fonte, namespace, procedimento ou bloco. Para obter mais informações, consulte [contextos de declaração e níveis de acesso padrão](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).  
  
 Na maioria das circunstâncias, você pode usar a primeira sintaxe na seção sintaxe deste tópico para declarar eventos. No entanto, alguns cenários exigem que você tenha mais controle sobre o comportamento detalhado de evento. A última sintaxe na seção Sintaxe neste tópico, que usa o `Custom` palavra-chave, fornece esse controle permitindo que você defina eventos personalizados. Em um evento personalizado, você pode especificar exatamente o que ocorre quando o código adiciona ou remove um manipulador de eventos para ou a partir do evento, ou quando o código gera o evento. Para obter exemplos, consulte [como: declarar eventos de personalizada para memória conservar](../../../visual-basic/programming-guide/language-features/events/how-to-declare-custom-events-to-conserve-memory.md) e [como: declarar personalizado eventos para evitar bloqueio](../../../visual-basic/programming-guide/language-features/events/how-to-declare-custom-events-to-avoid-blocking.md).  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir usa os eventos a contagem regressiva de 10 segundos para 0. O código ilustra várias instruções, propriedades e métodos relacionados a eventos. Isso inclui o `RaiseEvent` instrução.  
  
 A classe que gera um evento é a origem do evento e os métodos que processam o evento são os manipuladores de eventos. Uma fonte de evento pode ter vários manipuladores para eventos que ela gera. Quando a classe gera o evento, esse evento é gerado em cada classe que decidiu manipular eventos para essa instância do objeto.  
  
 O exemplo também usa um formulário (`Form1`) com um botão (`Button1`) e uma caixa de texto (`TextBox1`). Quando você clica no botão, a primeira caixa de texto exibe uma contagem regressiva de 10 para 0 segundos. Quando o tempo total (10 segundos) tiver decorrido, a primeira caixa de texto exibe "Concluído".  
  
 O código para `Form1` Especifica os estados iniciais e de terminal do formulário. Ele também contém o código executado quando os eventos são gerados.  
  
 Para usar este exemplo, abra um novo projeto de formulários do Windows. Em seguida, adicione um botão chamado `Button1` e uma caixa de texto denominada `TextBox1` ao formulário principal, chamado `Form1`. Em seguida, clique com botão direito do formulário e clique em **Exibir código** para abrir o editor de código.  
  
 Adicionar uma `WithEvents` à seção de declarações de variável de `Form1` classe:  
  
 [!code-vb[VbVbalrEvents&#14;](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/event-statement_2.vb)]  
  
 Adicione o seguinte código ao código para `Form1`. Substituir qualquer procedimentos duplicados que podem existir, como `Form_Load` ou `Button_Click`.  
  
 [!code-vb[VbVbalrEvents&#15;](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/event-statement_3.vb)]  
  
 Pressione F5 para executar o exemplo anterior e clique no botão **iniciar**. A primeira caixa de texto inicia a contagem regressiva de segundos. Quando o tempo total (10 segundos) tiver decorrido, a primeira caixa de texto exibe "Concluído".  
  
> [!NOTE]
>  O `My.Application.DoEvents` método não processa os eventos da mesma maneira que faz o formulário. Para habilitar o formulário manipular os eventos diretamente, você pode usar multithreading. Para obter mais informações, consulte [Threading](http://msdn.microsoft.com/library/552f6c68-dbdb-4327-ae36-32cf9063d88c).  
  
## <a name="see-also"></a>Consulte também  
 [Instrução RaiseEvent](../../../visual-basic/language-reference/statements/raiseevent-statement.md)   
 [Instrução Implements](../../../visual-basic/language-reference/statements/implements-statement.md)   
 [Eventos](../../../visual-basic/programming-guide/language-features/events/index.md)   
 [Instrução AddHandler](../../../visual-basic/language-reference/statements/addhandler-statement.md)   
 [Instrução RemoveHandler](../../../visual-basic/language-reference/statements/removehandler-statement.md)   
 [Identificadores](../../../visual-basic/language-reference/statements/handles-clause.md)   
 [Instrução delegate](../../../visual-basic/language-reference/statements/delegate-statement.md)   
 [Como: declarar eventos personalizados para conservar memória](../../../visual-basic/programming-guide/language-features/events/how-to-declare-custom-events-to-conserve-memory.md)   
 [Como: declarar eventos personalizados para evitar bloqueio](../../../visual-basic/programming-guide/language-features/events/how-to-declare-custom-events-to-avoid-blocking.md)   
 [Compartilhado](../../../visual-basic/language-reference/modifiers/shared.md)   
 [Sombras](../../../visual-basic/language-reference/modifiers/shadows.md)
