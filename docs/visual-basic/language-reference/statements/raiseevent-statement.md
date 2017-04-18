---
title: "Instrução RaiseEvent | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.RaiseEventMethod
- vb.RaiseEvent
- RaiseEvent
dev_langs:
- VB
helpviewer_keywords:
- raising events, RaiseEvent statement
- RaiseEvent statement
- event handlers, connecting events to
ms.assetid: f82e380a-1e6b-4047-bea8-c853f4d2c742
caps.latest.revision: 19
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
ms.openlocfilehash: 059b1347c4a35b896f5aa19cadb28fbceb8b25c9
ms.lasthandoff: 03/13/2017

---
# <a name="raiseevent-statement"></a>Instrução RaiseEvent
Gatilhos de um evento declarado no nível de módulo em uma classe, formulário ou documento.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
RaiseEvent eventname[( argumentlist )]  
```  
  
## <a name="parts"></a>Partes  
 `eventname`  
 Necessário. Nome do evento para disparar.  
  
 `argumentlist`  
 Opcional. Lista delimitada por vírgulas de variáveis, matrizes ou expressões. O `argumentlist` argumento deve ser delimitado por parênteses. Se não houver nenhum argumento, os parênteses devem ser omitidos.  
  
## <a name="remarks"></a>Comentários  
 Necessário `eventname` é o nome de um evento declarado dentro do módulo. Ele segue as convenções de nomenclatura de variável do Visual Basic.  
  
 Se o evento não foi declarado dentro do módulo no qual ele é disparado, ocorrerá um erro. O fragmento de código a seguir ilustra uma declaração de evento e um procedimento no qual o evento é gerado.  
  
 [!code-vb[VbVbalrEvents&#37;](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/raiseevent-statement_1.vb)]  
  
 Você não pode usar `RaiseEvent` para gerar eventos que não são explicitamente declarados no módulo. Por exemplo, todos os formulários herdam uma <xref:System.Windows.Forms.Control.Click>eventos de <xref:System.Windows.Forms.Form?displayProperty=fullName>, ele não pode ser gerado usando `RaiseEvent` em um formulário derivado.</xref:System.Windows.Forms.Form?displayProperty=fullName> </xref:System.Windows.Forms.Control.Click> Se você declarar uma `Click` eventos no módulo de formulário, ele shadows do formulário próprio <xref:System.Windows.Forms.Control.Click>evento.</xref:System.Windows.Forms.Control.Click> Você ainda pode invocar o formulário <xref:System.Windows.Forms.Control.Click>evento chamando o <xref:System.Windows.Forms.Control.OnClick%2A>método.</xref:System.Windows.Forms.Control.OnClick%2A> </xref:System.Windows.Forms.Control.Click>  
  
 Por padrão, um evento definido no Visual Basic gera seus manipuladores de eventos na ordem em que as conexões são estabelecidas. Como os eventos podem ter `ByRef` parâmetros, um processo que se conecta tardia pode receber parâmetros que foram alterados por um manipulador de eventos anterior. Depois de executar os manipuladores de eventos, o controle é retornado para a sub-rotina que gerou o evento.  
  
> [!NOTE]
>  Eventos não compartilhados não devem ser gerados dentro do construtor da classe em que elas são declaradas. Embora esses eventos não causam erros de tempo de execução, eles podem não ser detectadas por manipuladores de evento associado. Use o `Shared` modificador para criar um evento compartilhado, se você precisar disparar um evento de um construtor.  
  
> [!NOTE]
>  Você pode alterar o comportamento padrão de eventos definindo um evento personalizado. Para eventos personalizados, o `RaiseEvent` instrução chama o evento `RaiseEvent` acessador. Para obter mais informações sobre eventos personalizados, consulte [declaração de evento](../../../visual-basic/language-reference/statements/event-statement.md).  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir usa os eventos a contagem regressiva de 10 segundos para 0. O código ilustra vários métodos relacionados a eventos, propriedades e instruções, inclusive o `RaiseEvent` instrução.  
  
 A classe que gera um evento é a origem do evento e os métodos que processam o evento são os manipuladores de eventos. Uma fonte de evento pode ter vários manipuladores para eventos que ela gera. Quando a classe gera o evento, esse evento é gerado em cada classe que decidiu manipular eventos para essa instância do objeto.  
  
 O exemplo também usa um formulário (`Form1`) com um botão (`Button1`) e uma caixa de texto (`TextBox1`). Quando você clica no botão, a primeira caixa de texto exibe uma contagem regressiva de 10 para 0 segundos. Quando o tempo total (10 segundos) tiver decorrido, a primeira caixa de texto exibe "Concluído".  
  
 O código para `Form1` Especifica os estados iniciais e de terminal do formulário. Ele também contém o código executado quando os eventos são gerados.  
  
 Para usar esse exemplo, abra um novo projeto de aplicativo do Windows, adicione um botão chamado `Button1` e uma caixa de texto denominada `TextBox1` ao formulário principal, chamado `Form1`. Em seguida, clique com botão direito do formulário e clique em **Exibir código** para abrir o Editor de código.  
  
 Adicionar uma `WithEvents` à seção de declarações de variável de `Form1` classe.  
  
 [!code-vb[VbVbalrEvents&#14;](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/raiseevent-statement_2.vb)]  
  
## <a name="example"></a>Exemplo  
 Adicione o seguinte código ao código para `Form1`. Substituir qualquer procedimentos duplicados que podem existir, como `Form_Load`, ou `Button_Click`.  
  
 [!code-vb[VbVbalrEvents&#15;](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/raiseevent-statement_3.vb)]  
  
 Pressione F5 para executar o exemplo anterior e clique no botão **iniciar**. A primeira caixa de texto inicia a contagem regressiva de segundos. Quando o tempo total (10 segundos) tiver decorrido, a primeira caixa de texto exibe "Concluído".  
  
> [!NOTE]
>  O `My.Application.DoEvents` método não processa os eventos exatamente da mesma maneira como faz o formulário. Para permitir que o formulário para manipular os eventos diretamente, você pode usar multithreading. Para obter mais informações, consulte [Threading](http://msdn.microsoft.com/library/552f6c68-dbdb-4327-ae36-32cf9063d88c).  
  
## <a name="see-also"></a>Consulte também  
 [Eventos](../../../visual-basic/programming-guide/language-features/events/index.md)   
 [Instrução Event](../../../visual-basic/language-reference/statements/event-statement.md)   
 [Instrução AddHandler](../../../visual-basic/language-reference/statements/addhandler-statement.md)   
 [Instrução RemoveHandler](../../../visual-basic/language-reference/statements/removehandler-statement.md)   
 [Identificadores](../../../visual-basic/language-reference/statements/handles-clause.md)
