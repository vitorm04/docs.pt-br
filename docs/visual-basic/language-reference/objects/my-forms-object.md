---
title: Objeto My. Forms (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- My.Forms
- My.MyProject.Forms
helpviewer_keywords:
- My.Forms object
ms.assetid: f6bff4e6-6769-4294-956b-037aa6106d2a
ms.openlocfilehash: 9fa5c77dd12c98100e3d17fc473a6802180d1e32
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69965976"
---
# <a name="myforms-object"></a>Objeto My.Forms
Fornece propriedades para acessar uma instância de cada formulário do Windows declarado no projeto atual.  
  
## <a name="remarks"></a>Comentários  
 O `My.Forms` objeto fornece uma instância de cada formulário no projeto atual. O nome da propriedade é o mesmo que o nome do formulário que a propriedade acessa.   
  
 Você pode acessar os formulários fornecidos pelo `My.Forms` objeto usando o nome do formulário, sem qualificação. Como o nome da propriedade é igual ao nome do tipo do formulário, isso permite que você acesse um formulário como se ele tivesse uma instância padrão. Por exemplo, `My.Forms.Form1.Show` equivale a `Form1.Show`.  
  
 O `My.Forms` objeto expõe apenas os formulários associados ao projeto atual. Ele não fornece acesso a formulários declarados em DLLs referenciadas. Para acessar um formulário que uma DLL fornece, você deve usar o nome qualificado do formulário, escrito como *DllName*. *FormName*.  
  
 Você pode usar a <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OpenForms%2A> propriedade para obter uma coleção de todos os formulários abertos do aplicativo.  
  
 O objeto e suas propriedades estão disponíveis apenas para aplicativos do Windows.  
  
## <a name="properties"></a>Propriedades  
 Cada propriedade do `My.Forms` objeto fornece acesso a uma instância de um formulário no projeto atual. O nome da propriedade é o mesmo que o nome do formulário que a propriedade acessa, e o tipo de propriedade é o mesmo que o tipo do formulário.  
  
> [!NOTE]
> Se houver uma colisão de nomes, o nome da propriedade para acessar um formulário será *RootNamespace*_*namespace*\_*FormName*. Por exemplo, considere dois formulários chamados `Form1.`se um desses formulários estiver no namespace `WindowsApplication1` raiz e no namespace `Namespace1`, você acessaria esse formulário por meio `My.Forms.WindowsApplication1_Namespace1_Form1`do.  
  
 O `My.Forms` objeto fornece acesso à instância do formulário principal do aplicativo que foi criado na inicialização. Para todos os outros formulários, `My.Forms` o objeto cria uma nova instância do formulário quando ele é acessado e armazena-o. As tentativas subsequentes de acessar essa propriedade retornam essa instância do formulário.  
  
 Você pode descartar um formulário atribuindo `Nothing` à propriedade para esse formulário. O setter da propriedade chama <xref:System.Windows.Forms.Form.Close%2A> o método do formulário e, em seguida, `Nothing` atribui ao valor armazenado. Se você atribuir qualquer valor diferente `Nothing` de à propriedade, o setter lançará uma <xref:System.ArgumentException> exceção.  
  
 Você pode testar se uma propriedade do `My.Forms` objeto armazena uma instância do formulário usando o `Is` operador or `IsNot` . Você pode usar esses operadores para verificar se o valor da propriedade é `Nothing`.  
  
> [!NOTE]
> Normalmente, o `Is` operador `IsNot` or precisa ler o valor da propriedade para executar a comparação. No entanto, se a propriedade `Nothing`atualmente armazena, a propriedade cria uma nova instância do formulário e, em seguida, retorna essa instância. No entanto, o compilador de Visual Basic trata as `My.Forms` Propriedades do objeto de forma `Is` diferente `IsNot` e permite que o operador OR Verifique o status da propriedade sem alterar seu valor.  
  
## <a name="example"></a>Exemplo  
 Este exemplo altera o título do formulário padrão `SidebarMenu` .  
  
 [!code-vb[VbVbalrMyForms#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyForms/VB/Class1.vb#2)]  
  
 Para que este exemplo funcione, seu projeto deve ter um formulário chamado `SidebarMenu`.  
  
 Esse código só funcionará em um projeto de aplicativo do Windows.  
  
## <a name="requirements"></a>Requisitos  
  
### <a name="availability-by-project-type"></a>Disponibilidade por tipo de projeto  
  
|Tipo de projeto|Disponível|  
|---|---|  
|Aplicativo do Windows|**Sim**|  
|Biblioteca de Classes|Não|  
|Aplicativo do Console|Não|  
|Biblioteca de controle do Windows|Não|  
|Biblioteca de controle da Web|Não|  
|Serviço do Windows|Não|  
|Site da Web|Não|  
  
## <a name="see-also"></a>Consulte também

- <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OpenForms%2A>
- <xref:System.Windows.Forms.Form>
- <xref:System.Windows.Forms.Form.Close%2A>
- [Objetos](../../../visual-basic/language-reference/objects/index.md)
- [Operador Is](../../../visual-basic/language-reference/operators/is-operator.md)
- [Operador IsNot](../../../visual-basic/language-reference/operators/isnot-operator.md)
- [Acessando formulários de aplicativo](../../../visual-basic/developing-apps/programming/accessing-application-forms.md)
