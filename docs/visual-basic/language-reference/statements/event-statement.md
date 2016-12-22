---
title: "Instru&#231;&#227;o Event | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vb.Event"
  - "vb.Custom"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "Palavra-chave ByRef, instruções Event"
  - "Palavra-chave ByVal, instruções Event"
  - "palavras-chave Custom"
  - "declarações, eventos"
  - "declarando eventos, sintaxe"
  - "declarando eventos definidos pelo usuário"
  - "palavra-chave event [Visual Basic]"
  - "instrução Event"
  - "eventos [Visual Basic], personalizado"
  - "eventos [Visual Basic], declarando"
  - "palavra-chave Public, instruções Event"
  - "Palavra-chave WithEvents, instruções Event"
ms.assetid: 306ff8ed-74dd-4b6a-bd2f-e91b17474042
caps.latest.revision: 33
caps.handback.revision: 33
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Instru&#231;&#227;o Event
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Declara um evento definido pelo usuário.  
  
## Sintaxe  
  
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
  
## Partes  
  
|||  
|-|-|  
|Parte|Descrição|  
|`attrlist`|Opcional.  Lista de atributos que se aplicam a esse evento.  Vários atributos são separados por vírgulas.  Você deve colocar o [Lista de atributos](../../../visual-basic/language-reference/statements/attribute-list.md) entre colchetes angulares \("`<`"e"`>`"\).|  
|`accessmodifier`|Opcional.  Especifica qual código pode acessar o evento.  Pode ser uma das seguintes opções:<br /><br /> -   [Públicas](../../../visual-basic/language-reference/modifiers/public.md)— qualquer código que pode acessar o elemento que o declara pode acessá\-lo.<br />-   [Protegido](../../../visual-basic/language-reference/modifiers/protected.md)— apenas código dentro de sua classe ou uma classe derivada pode acessá\-lo.<br />-   [Amigo](../../../visual-basic/language-reference/modifiers/friend.md)— apenas código no mesmo conjunto pode acessá\-lo.<br />-   [Particular](../../../visual-basic/language-reference/modifiers/private.md)— apenas código no mesmo elemento que o declara pode acessá\-lo.<br /><br /> Você pode especificar `Protected Friend` para habilitar o acesso do código de classe do evento, uma classe derivada ou o mesmo assembly.|  
|`Shared`|Opcional.  Especifica que este evento não está associado uma instância específica de uma classe ou estrutura.|  
|`Shadows`|Opcional.  Indica que este evento redeclara e oculta um elemento de programação de nome idêntico, ou conjunto de elementos sobrecarregados, na classe base.  Você pode sombrear qualquer tipo de elemento declarado com qualquer outro tipo.<br /><br /> Um elemento sombreado não está disponível de dentro da classe derivada que o sombreia, com exceção de onde o elemento sombreamento é inacessível.  Por exemplo, se um `Private` elemento sombreia um elemento de classe base, o código que não tem permissão para acessar o `Private` elemento acessa o elemento da classe base em vez disso.|  
|`eventname`|Obrigatório.  Nome do evento; segue convenções de nomenclatura de variável padrão.|  
|`parameterlist`|Opcional.  Lista de locais variáveis que representam os parâmetros desse evento.  Você deve colocar o [Lista de parâmetros](../../../visual-basic/language-reference/statements/parameter-list.md) entre parênteses.|  
|`Implements`|Opcional.  Indica que este evento implementa um evento de uma interface.|  
|`implementslist`|Necessário se `Implements` for fornecido.  Lista de `Sub` procedimentos que estão sendo implementados.  Vários procedimentos são separados por vírgulas:<br /><br /> *implementedprocedure* \[, *implementedprocedure* ...  \]<br /><br /> Cada `implementedprocedure` tem a seguinte sintaxe e partes:<br /><br /> `interface`.`definedname`<br /><br /> -   `interface` \-Necessário.  Nome de uma interface que este procedimento do que contém a classe ou estrutura está implementando.<br />-   `Definedname` \-Necessário.  Nome pelo qual o procedimento é definido em `interface`.  Isso não precisa ser o mesmo que `name`, o nome que está usando este procedimento para implementar o procedimento definido.|  
|`Custom`|Obrigatório.  Eventos declarados como `Custom` deve definir personalizado `AddHandler`, `RemoveHandler`, e `RaiseEvent` acessadores.|  
|`delegatename`|Opcional.  O nome de um delegado que especifica a assinatura do manipulador de eventos.|  
|`AddHandler`|Obrigatório.  Declara um `AddHandler` acessador, que especifica as instruções para executar quando um manipulador de eventos é adicionado, explicitamente usando o `AddHandler` instrução ou implicitamente, usando o `Handles` cláusula.|  
|`End AddHandler`|Obrigatório.  Encerra o `AddHandler` bloco.|  
|`value`|Obrigatório.  Nome do parâmetro.|  
|`RemoveHandler`|Obrigatório.  Declara um `RemoveHandler` acessador, que especifica as instruções para executar quando um manipulador de eventos for removido usando o `RemoveHandler` instrução.|  
|`End RemoveHandler`|Obrigatório.  Encerra o `RemoveHandler` bloco.|  
|`RaiseEvent`|Obrigatório.  Declara um `RaiseEvent` acessador, que especifica as instruções para executar quando o evento é gerado usando o `RaiseEvent` instrução.  Normalmente, isso invoca uma lista dos representantes mantido pela `AddHandler` e `RemoveHandler` acessadores.|  
|`End RaiseEvent`|Obrigatório.  Encerra o `RaiseEvent` bloco.|  
|`delegatesignature`|Obrigatório.  Lista de parâmetros que corresponde aos parâmetros exigidos pelo `delegatename` delegar.  Você deve colocar o [Lista de parâmetros](../../../visual-basic/language-reference/statements/parameter-list.md) entre parênteses.|  
|`statements`|Opcional.  Instruções que contêm o corpo do `AddHandler`, `RemoveHandler`, e `RaiseEvent` métodos.|  
|`End Event`|Obrigatório.  Encerra o `Event` bloco.|  
  
## Comentários  
 Depois que o evento foi declarado, use o `RaiseEvent` instrução para gerar o evento.  Um evento típico pode ser declarado e levantado conforme os seguintes fragmentos:  
  
 [!code-vb[VbVbalrEvents#13](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/event-statement_1.vb)]  
  
> [!NOTE]
>  Você pode declarar argumentos de evento, como você faz argumentos de procedimentos, com as seguintes exceções: eventos não podem ter argumentos nomeados, `ParamArray` argumentos, ou `Optional` argumentos.  Eventos não têm valores de retorno.  
  
 Para manipular um evento, você deve associá\-lo com um manipulador de eventos sub\-rotina usando a `Handles` ou `AddHandler` instrução.  As assinaturas de sub\-rotina e o evento devem corresponder.  Para manipular um evento compartilhado, você deve usar o `AddHandler` instrução.  
  
 Você pode usar `Event` apenas no nível de módulo.  Isso significa que o *contexto declaração* para um evento deve ser uma classe, estrutura, módulo ou interface e não pode ser um arquivo fonte, namespace, procedimento ou bloco.  Para obter mais informações, consulte [Contextos de declaração e níveis de acesso padrão](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).  
  
 Na maioria das circunstâncias, você pode usar a primeira sintaxe na seção sintaxe deste tópico para declarar eventos.  No entanto, alguns cenários exigem que você tenha mais controle sobre o comportamento detalhado de evento.  A última sintaxe na seção sintaxe deste tópico, que usa o `Custom` palavra\-chave, fornece esse controle permitindo que você defina eventos personalizados.  Em um evento personalizado, você pode especificar exatamente o que ocorre quando o código adiciona ou remove um manipulador de eventos para ou a partir do evento, ou quando o código gera o evento.  Para obter exemplos, consulte [Como declarar eventos personalizados para conservar memória](../../../visual-basic/programming-guide/language-features/events/how-to-declare-custom-events-to-conserve-memory.md) e [Como declarar eventos personalizados para evitar bloqueio](../../../visual-basic/programming-guide/language-features/events/how-to-declare-custom-events-to-avoid-blocking.md).  
  
## Exemplo  
 O exemplo a seguir usa os eventos a contagem regressiva de 10 segundos para 0.  O código ilustra várias instruções, propriedades e métodos relacionados a eventos.  Isso inclui o `RaiseEvent` instrução.  
  
 A classe que gera um evento é a origem do evento e os métodos que processam o evento são os manipuladores de eventos.  Uma fonte de evento pode ter vários manipuladores para eventos que ela gera.  Quando a classe gera o evento, esse evento é gerado em cada classe que decidiu manipular eventos para essa instância do objeto.  
  
 O exemplo também usa um formulário \(`Form1`\) com um botão \(`Button1`\) e uma caixa de texto \(`TextBox1`\).  Quando você clica no botão, a primeira caixa de texto exibe uma contagem regressiva de 10 para 0 segundos.  Quando o tempo total \(10 segundos\) tiver decorrido, a primeira caixa de texto exibe "Concluído".  
  
 O código para `Form1` Especifica os estados iniciais e de terminal do formulário.  Ela também contém o código executado quando os eventos são gerados.  
  
 Para usar este exemplo, abra um novo projeto Windows Forms.  Em seguida, adicione um botão chamado `Button1` e uma caixa de texto denominada `TextBox1` ao formulário principal, chamado `Form1`.  Em seguida, clique com botão direito do formulário e clique em **Exibir código** para abrir o editor de código.  
  
 Adicione um `WithEvents` à seção de declarações de variável de `Form1` classe:  
  
 [!code-vb[VbVbalrEvents#14](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/event-statement_2.vb)]  
  
 Adicione o seguinte código para o código `Form1`.  Substituir qualquer procedimentos duplicados que podem existir, como `Form_Load` ou `Button_Click`.  
  
 [!code-vb[VbVbalrEvents#15](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/event-statement_3.vb)]  
  
 Pressione F5 para executar o exemplo anterior e clique no botão **Iniciar**.  A primeira caixa de texto inicia a contagem regressiva de segundos.  Quando o tempo total \(10 segundos\) tiver decorrido, a primeira caixa de texto exibe "Concluído".  
  
> [!NOTE]
>  O `My.Application.DoEvents` método não processa os eventos da mesma maneira que faz o formulário.  Para habilitar o formulário manipular os eventos diretamente, você pode usar multithreading.  Para obter mais informações, consulte [Threading](../Topic/Threading%20\(C%23%20and%20Visual%20Basic\).md).  
  
## Consulte também  
 [Instrução RaiseEvent](../../../visual-basic/language-reference/statements/raiseevent-statement.md)   
 [Instrução Implements](../../../visual-basic/language-reference/statements/implements-statement.md)   
 [Eventos](../../../visual-basic/programming-guide/language-features/events/events.md)   
 [Instrução AddHandler](../../../visual-basic/language-reference/statements/addhandler-statement.md)   
 [Instrução RemoveHandler](../../../visual-basic/language-reference/statements/removehandler-statement.md)   
 [Handles](../../../visual-basic/language-reference/statements/handles-clause.md)   
 [Instrução Delegate](../../../visual-basic/language-reference/statements/delegate-statement.md)   
 [Como declarar eventos personalizados para conservar memória](../../../visual-basic/programming-guide/language-features/events/how-to-declare-custom-events-to-conserve-memory.md)   
 [Como declarar eventos personalizados para evitar bloqueio](../../../visual-basic/programming-guide/language-features/events/how-to-declare-custom-events-to-avoid-blocking.md)   
 [Compartilhado](../../../visual-basic/language-reference/modifiers/shared.md)   
 [Sombras](../../../visual-basic/language-reference/modifiers/shadows.md)