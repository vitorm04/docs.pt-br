---
title: "Objeto My.Forms | Microsoft Docs"
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
  - "My.Forms"
  - "My.MyProject.Forms"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "Objeto My.Forms"
ms.assetid: f6bff4e6-6769-4294-956b-037aa6106d2a
caps.latest.revision: 22
caps.handback.revision: 22
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Objeto My.Forms
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Fornece propriedades para acessar uma instância de cada Windows form declarado no projeto atual.  
  
## Comentários  
 O `My.Forms` objeto fornece uma instância de cada formulário no projeto atual.  O nome da propriedade é o mesmo que o nome do formulário que a acessa a propriedade.  Para obter informações sobre como adicionar formulários a um projeto, consulte [How to: Add Windows Forms to a Project](http://msdn.microsoft.com/pt-br/3d7bb25f-fd90-47cf-9378-fa0d764686c1).  
  
 Você pode acessar os formulários fornecidos pelo `My.Forms` o objeto usando o nome do formulário, sem qualificação.  Como o nome da propriedade é igual ao nome do tipo do formulário, isso permite que você acesse um formulário como se ela fosse uma instância padrão.  Por exemplo, `My.Forms.Form1.Show` é equivalente a `Form1.Show`.  
  
 O `My.Forms` objeto expõe apenas os formulários associados ao projeto atual.  Ele não fornece acesso aos formulários declarado em DLLs referenciadas.  Para acessar um formulário que fornece a uma DLL, você deve usar o nome qualificado do formulário, escrito como  *DllName*. *Nomedoformulário*.  
  
 Você pode usar o <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OpenForms%2A> propriedade para obter uma coleção de todos os formulários abertos do aplicativo.  
  
 O objeto e suas propriedades estão disponíveis somente para aplicativos do Windows.  
  
## Propriedades  
 Cada propriedade da `My.Forms` objeto fornece acesso a uma instância de um formulário no projeto atual.  O nome da propriedade é o mesmo que o nome do formulário que a acessa a propriedade e o tipo de propriedade é o mesmo que o tipo do formulário.  
  
> [!NOTE]
>  Se houver um conflito de nome, o nome da propriedade para acessar um formulário é  *RootNamespace*\_*espaço para nome*\_*nomedoformulário*.  Por exemplo, considere os dois formulários denominados `Form1.`se um desses formulários está no namespace raiz `WindowsApplication1` e no namespace `Namespace1`, você pode acessar o formulário por meio de `My.Forms.WindowsApplication1_Namespace1_Form1`.  
  
 O `My.Forms` objeto fornece acesso à instância do formulário principal do aplicativo, que foi criado na inicialização.  Para todos os outros formulários, o `My.Forms` objeto cria uma nova instância do formulário quando ele é acessado e o armazena.  Tentativas subseqüentes para acessar essa propriedade retornará a essa instância do formulário.  
  
 Você pode dispor de um formulário atribuindo `Nothing` para a propriedade desse formulário.  As chamadas de setter de propriedade da <xref:System.Windows.Forms.Form.Close%2A> o método do formulário e, em seguida, atribui `Nothing` para o valor armazenado.  Se você atribuir qualquer valor diferente de `Nothing` à propriedade, o setter lança um <xref:System.ArgumentException> exceção.  
  
 Você pode testar se uma propriedade da `My.Forms` objeto armazena uma instância do formulário usando o `Is` ou `IsNot` operador.  Você pode usar esses operadores para verificar se o valor da propriedade é `Nothing`.  
  
> [!NOTE]
>  Normalmente, o `Is` ou `IsNot` operador tem que ler o valor da propriedade para executar a comparação.  No entanto, se a propriedade atualmente armazena `Nothing`, a propriedade cria uma nova instância do formulário e, em seguida, retorna essa instância.  No entanto, o compilador Visual Basic trata as propriedades da `My.Forms` objeto de forma diferente e permite que o `Is` ou `IsNot` operador para verificar o status da propriedade sem alterar seu valor.  
  
## Exemplo  
 Este exemplo altera o título do padrão `SidebarMenu` formulário.  
  
 [!code-vb[VbVbalrMyForms#2](../../../visual-basic/language-reference/objects/codesnippet/VisualBasic/my-forms-object_1.vb)]  
  
 Para esse exemplo funcione, seu projeto deve ter um formulário denominado `SidebarMenu`.  Para obter mais informações, consulte [How to: Add Windows Forms to a Project](http://msdn.microsoft.com/pt-br/3d7bb25f-fd90-47cf-9378-fa0d764686c1).  
  
 Esse código funciona apenas em um projeto Windows Application.  
  
## Requisitos  
  
### Disponibilidade por Tipo de Projeto  
  
|||  
|-|-|  
|Tipo de Projeto|Disponível|  
|Aplicativo do Windows|**Sim**|  
|Biblioteca de Classe|Não|  
|Aplicativo de Console|Não|  
|Biblioteca de Controle do Windows|Não|  
|Biblioteca de Controle da Web|Não|  
|Serviço do Windows|Não|  
|Site|Não|  
  
## Consulte também  
 <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OpenForms%2A>   
 <xref:System.Windows.Forms.Form>   
 <xref:System.Windows.Forms.Form.Close%2A>   
 [Objetos ](../../../visual-basic/language-reference/objects/index.md)   
 [How to: Add Windows Forms to a Project](http://msdn.microsoft.com/pt-br/3d7bb25f-fd90-47cf-9378-fa0d764686c1)   
 [Operador Is](../../../visual-basic/language-reference/operators/is-operator.md)   
 [Operador IsNot](../../../visual-basic/language-reference/operators/isnot-operator.md)   
 [Acessando formulários de aplicativo](../../../visual-basic/developing-apps/programming/accessing-application-forms.md)