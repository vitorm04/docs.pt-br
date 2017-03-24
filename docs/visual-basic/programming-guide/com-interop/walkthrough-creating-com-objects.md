---
title: 'Passo a passo: Criando objetos COM o Visual Basic | Documentos do Microsoft'
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- COM interop, creating COM objects
- COM objects, creating
- COM interop, walkthroughs
- object creation, COM objects
- COM objects, walkthroughs
ms.assetid: 7b07a463-bc72-4392-9ba0-9dfcb697a44f
caps.latest.revision: 30
author: stevehoag
ms.author: shoag
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
ms.openlocfilehash: cce28e2be5914880107334bf2c4dc4dc645b4793
ms.lasthandoff: 03/13/2017

---
# <a name="walkthrough-creating-com-objects-with-visual-basic"></a>Instruções passo a passo: criando objetos COM com o Visual Basic
Ao criar novos aplicativos ou componentes, é melhor criar assemblies do .NET Framework. No entanto, [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] também facilita a expor um componente do .NET Framework para COM. Isso permite que você fornecer novos componentes anteriores aplicativo conjuntos que requerem componentes COM. Este passo a passo demonstra como usar [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] para expor [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)] objetos como objetos COM, com e sem o modelo de classe COM.  
  
 A maneira mais fácil expor objetos COM é usando o modelo de classe COM. O modelo de classe COM cria uma nova classe e, em seguida, configura seu projeto para gerar a camada de classe e interoperabilidade como um objeto COM e registrá-lo com o sistema operacional.  
  
> [!NOTE]
>  Embora você também pode expor uma classe criada em [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] como um objeto COM para código não gerenciado usar, ele não é uma verdadeiro COM objeto e não pode ser usado por [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]. Para obter mais informações, consulte [interoperabilidade COM em aplicativos do .NET Framework](../../../visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications.md).  
  
[!INCLUDE[note_settings_general](../../../csharp/language-reference/compiler-messages/includes/note_settings_general_md.md)]  
  
### <a name="to-create-a-com-object-by-using-the-com-class-template"></a>Para criar um objeto COM usando o modelo de classe COM  
  
1.  Abra um novo projeto de aplicativo do Windows a partir de **arquivo** menu clicando **novo projeto**.  
  
2.  No **novo projeto** caixa de diálogo sob o **tipos de projeto** campo, verifique que o Windows está selecionado. Selecione **biblioteca de classes** do **modelos** lista e, em seguida, clique em **Okey**. O novo projeto é exibido.  
  
3.  Selecione **Adicionar Novo Item** do **projeto** menu. A caixa de diálogo **Adicionar Novo Item** é exibida.  
  
4.  Selecione **classe COM** do **modelos** lista e, em seguida, clique em **adicionar**. [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]Adiciona uma nova classe e configura o novo projeto para interoperabilidade COM.  
  
5.  Adicione código como propriedades, métodos e eventos à classe COM.  
  
6.  Selecione **criar ClassLibrary1** do **criar** menu. [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]cria o assembly e registra o objeto COM o sistema operacional.  
  
## <a name="creating-com-objects-without-the-com-class-template"></a>Criando objetos sem o modelo de classe COM  
 Você também pode criar uma classe COM manualmente em vez de usar o modelo de classe COM. Esse procedimento é útil quando você está trabalhando na linha de comando ou quando você deseja maior controle sobre como os objetos são definidos.  
  
#### <a name="to-set-up-your-project-to-generate-a-com-object"></a>Para configurar seu projeto para gerar um objeto COM  
  
1.  Abra um novo projeto de aplicativo do Windows a partir de **arquivo** menu clicando **NewProject**.  
  
2.  No **novo projeto** caixa de diálogo sob o **tipos de projeto** campo, verifique que o Windows está selecionado. Selecione **biblioteca de classes** do **modelos** lista e, em seguida, clique em **Okey**. O novo projeto é exibido.  
  
3.  Em **Solution Explorer**, clique em seu projeto e, em seguida, clique em **propriedades**. O **Project Designer** é exibida.  
  
4.  Clique na guia **Compilar**.  
  
5.  Selecione o **Register for COM Interop** caixa de seleção.  
  
#### <a name="to-set-up-the-code-in-your-class-to-create-a-com-object"></a>Para configurar o código em sua classe para criar um objeto COM  
  
1.  Em **Solution Explorer**, clique duas vezes em **Class1. vb** para exibir seu código.  
  
2.  Renomeie a classe para `ComClass1`.  
  
3.  Adicione as seguintes constantes para `ComClass1`. Eles armazenará as constantes de identificador globalmente exclusivo (GUID) que os objetos COM são necessários.  
  
     [!code-vb[VbVbalrInterop n º&2;](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-creating-com-objects_1.vb)]  
  
4.  Sobre o **ferramentas** menu, clique em **criar Guid**. No **criar GUID** caixa de diálogo, clique em **formato do registro** e, em seguida, clique em **cópia**. Clique em **Sair**.  
  
5.  Substitua a cadeia de caracteres vazia para o `ClassId` com o GUID, removendo à esquerda e à direita chaves. Por exemplo, se o GUID fornecido pelo Guidgen é `"{2C8B0AEE-02C9-486e-B809-C780A11530FE}"` , em seguida, seu código deve aparecer da seguinte maneira.  
  
     [!code-vb[VbVbalrInterop n º&3;](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-creating-com-objects_2.vb)]  
  
6.  Repita as etapas anteriores para o `InterfaceId` e `EventsId` constantes, como no exemplo a seguir.  
  
     [!code-vb[VbVbalrInterop n º&4;](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-creating-com-objects_3.vb)]  
  
    > [!NOTE]
    >  Certifique-se de que os GUIDs são novas e exclusivas; Caso contrário, o componente COM pode entrar em conflito com outros componentes COM.  
  
7.  Adicionar o `ComClass` atributo `ComClass1`, especificando os GUIDs para a identificação de classe, Interface ID e identificação de eventos como no exemplo a seguir:  
  
     [!code-vb[VbVbalrInterop n º&5;](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-creating-com-objects_4.vb)]  
  
8.  Classes COM devem ter um sem parâmetros `Public Sub New()` construtor, ou a classe não registrará corretamente. Adicione um construtor sem parâmetros à classe:  
  
     [!code-vb[VbVbalrInterop n º&6;](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-creating-com-objects_5.vb)]  
  
9. Adicione propriedades, métodos e eventos à classe, terminando com um `End Class` instrução. Selecione **Build Solution** do **criar** menu. [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]cria o assembly e registra o objeto COM o sistema operacional.  
  
    > [!NOTE]
    >  Os objetos COM que você gerar com [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] não pode ser usado por outros [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] aplicativos porque eles não são objetos true. Tenta adicionar referências a esses objetos COM irá gerar um erro. Para obter detalhes, consulte [interoperabilidade COM em aplicativos do .NET Framework](../../../visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications.md).  
  
## <a name="see-also"></a>Consulte também  
 <xref:Microsoft.VisualBasic.ComClassAttribute></xref:Microsoft.VisualBasic.ComClassAttribute>   
 [Interoperabilidade COM](../../../visual-basic/programming-guide/com-interop/index.md)   
 [Passo a passo: Implementando a herança com objetos COM](../../../visual-basic/programming-guide/com-interop/walkthrough-implementing-inheritance-with-com-objects.md)   
 [Diretiva #Region](../../../visual-basic/language-reference/directives/region-directive.md)   
 [Interoperabilidade COM em aplicativos do .NET Framework](../../../visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications.md)   
 [Solução de problemas de Interoperabilidade](../../../visual-basic/programming-guide/com-interop/troubleshooting-interoperability.md)
