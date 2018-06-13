---
title: 'Instruções passo a passo: criando objetos COM com o Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- COM interop [Visual Basic], creating COM objects
- COM objects, creating
- COM interop [Visual Basic], walkthroughs
- object creation [Visual Basic], COM objects
- COM objects, walkthroughs
ms.assetid: 7b07a463-bc72-4392-9ba0-9dfcb697a44f
ms.openlocfilehash: caf0a071d65746f1027052e648ade538d62dc4bb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33643855"
---
# <a name="walkthrough-creating-com-objects-with-visual-basic"></a>Instruções passo a passo: criando objetos COM com o Visual Basic
Ao criar novos aplicativos ou componentes, é melhor criar assemblies do .NET Framework. No entanto, Visual Basic também facilita a expor um componente do .NET Framework para COM. Isso permite que você fornecer novos componentes anteriores aplicativo conjuntos que requerem componentes COM. Este passo a passo demonstra como usar o Visual Basic para expor [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] objetos como objetos COM, com e sem o modelo de classe COM.  
  
 A maneira mais fácil expor objetos COM é usando o modelo de classe COM. O modelo de classe COM cria uma nova classe e, em seguida, configura seu projeto para gerar a camada de classe e interoperabilidade como um objeto COM e registrá-lo com o sistema operacional.  
  
> [!NOTE]
>  Embora você também pode expor uma classe criada no Visual Basic como um objeto COM para código não gerenciado usar, ele não é um objeto COM true e não pode ser usado pelo Visual Basic. Para obter mais informações, consulte [interoperabilidade COM em aplicativos do .NET Framework](../../../visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications.md).  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-create-a-com-object-by-using-the-com-class-template"></a>Para criar um objeto COM usando o modelo de classe COM  
  
1.  Abra um novo projeto de aplicativo do Windows a partir de **arquivo** menu clicando **novo projeto**.  
  
2.  No **novo projeto** caixa de diálogo do **tipos de projeto** campo, verifique se o Windows está selecionado. Selecione **biblioteca de classes** do **modelos** lista e, em seguida, clique em **Okey**. O novo projeto é exibido.  
  
3.  Selecione **Adicionar Novo Item** do **projeto** menu. A caixa de diálogo **Adicionar Novo Item** é exibida.  
  
4.  Selecione **classe COM** do **modelos** lista e, em seguida, clique em **adicionar**. Visual Basic adiciona uma nova classe e configura o novo projeto para interoperabilidade COM.  
  
5.  Adicione código como propriedades, métodos e eventos para a classe COM.  
  
6.  Selecione **criar ClassLibrary1** do **criar** menu. Visual Basic cria o assembly e registra o objeto COM o sistema operacional.  
  
## <a name="creating-com-objects-without-the-com-class-template"></a>Criando objetos sem o modelo de classe COM  
 Você também pode criar uma classe COM manualmente, em vez de usar o modelo de classe COM. Esse procedimento é útil quando você estiver trabalhando na linha de comando ou quando você quiser mais controle sobre como os objetos são definidos.  
  
#### <a name="to-set-up-your-project-to-generate-a-com-object"></a>Para configurar seu projeto para gerar um objeto COM  
  
1.  Abra um novo projeto de aplicativo do Windows a partir de **arquivo** menu clicando **NewProject**.  
  
2.  No **novo projeto** caixa de diálogo do **tipos de projeto** campo, verifique se o Windows está selecionado. Selecione **biblioteca de classes** do **modelos** lista e, em seguida, clique em **Okey**. O novo projeto é exibido.  
  
3.  Em **Solution Explorer**, clique com o botão direito e, em seguida, clique em **propriedades**. O **Project Designer** é exibido.  
  
4.  Clique na guia **Compilar**.  
  
5.  Selecione o **registrar para interoperabilidade COM** caixa de seleção.  
  
#### <a name="to-set-up-the-code-in-your-class-to-create-a-com-object"></a>Para configurar o código em sua classe para criar um objeto COM  
  
1.  Em **Solution Explorer**, clique duas vezes em **Class1** para exibir seu código.  
  
2.  Renomeie a classe para `ComClass1`.  
  
3.  Adicione as seguintes constantes para `ComClass1`. Eles armazenará as constantes de identificador globalmente exclusivo (GUID) que os objetos COM devem ter.  
  
     [!code-vb[VbVbalrInterop#2](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-creating-com-objects_1.vb)]  
  
4.  No menu **Ferramentas**, clique em **Criar GUID**. Na caixa de diálogo **Criar GUID**, clique em **Formato do Registro** e clique em **Copiar**. Clique em **Sair**.  
  
5.  Substitua a cadeia de caracteres vazia para o `ClassId` com o GUID, chaves removendo à esquerda e à direita. Por exemplo, se o GUID fornecido pelo Guidgen é `"{2C8B0AEE-02C9-486e-B809-C780A11530FE}"` , em seguida, seu código deve aparecer da seguinte maneira.  
  
     [!code-vb[VbVbalrInterop#3](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-creating-com-objects_2.vb)]  
  
6.  Repita as etapas anteriores para o `InterfaceId` e `EventsId` constantes, como no exemplo a seguir.  
  
     [!code-vb[VbVbalrInterop#4](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-creating-com-objects_3.vb)]  
  
    > [!NOTE]
    >  Certifique-se de que os GUIDs são novos e exclusivos; Caso contrário, o componente COM pode entrar em conflito com outros componentes COM.  
  
7.  Adicionar o `ComClass` atributo `ComClass1`, especificando os GUIDs para a identificação de classe, a ID de Interface e a ID de eventos, como no exemplo a seguir:  
  
     [!code-vb[VbVbalrInterop#5](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-creating-com-objects_4.vb)]  
  
8.  Classes COM devem ter um sem parâmetros `Public Sub New()` construtor, ou a classe não registrará corretamente. Adicione um construtor sem parâmetros à classe:  
  
     [!code-vb[VbVbalrInterop#6](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-creating-com-objects_5.vb)]  
  
9. Adicionar propriedades, métodos e eventos à classe, terminando com um `End Class` instrução. Selecione **compilar solução** do **criar** menu. Visual Basic cria o assembly e registra o objeto COM o sistema operacional.  
  
    > [!NOTE]
    >  Os objetos COM que você gerar com o Visual Basic não podem ser usados por outros aplicativos do Visual Basic, porque eles não são objetos true. Tenta adicionar referências a esses objetos COM irá gerar um erro. Para obter detalhes, consulte [interoperabilidade COM em aplicativos do .NET Framework](../../../visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications.md).  
  
## <a name="see-also"></a>Consulte também  
 <xref:Microsoft.VisualBasic.ComClassAttribute>  
 [Interoperabilidade COM](../../../visual-basic/programming-guide/com-interop/index.md)  
 [Instruções passo a passo: implementando a herança com objetos COM](../../../visual-basic/programming-guide/com-interop/walkthrough-implementing-inheritance-with-com-objects.md)  
 [Diretiva #Region](../../../visual-basic/language-reference/directives/region-directive.md)  
 [Interoperabilidade COM em Aplicativos .NET Framework](../../../visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications.md)  
 [Solução de problemas de Interoperabilidade](../../../visual-basic/programming-guide/com-interop/troubleshooting-interoperability.md)
