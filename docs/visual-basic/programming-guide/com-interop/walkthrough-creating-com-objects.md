---
title: 'Passo a passo: Criando objetos COM o Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- COM interop [Visual Basic], creating COM objects
- COM objects, creating
- COM interop [Visual Basic], walkthroughs
- object creation [Visual Basic], COM objects
- COM objects, walkthroughs
ms.assetid: 7b07a463-bc72-4392-9ba0-9dfcb697a44f
ms.openlocfilehash: 97e917d568b31860979e54598350d1ae7a6fdb25
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62022305"
---
# <a name="walkthrough-creating-com-objects-with-visual-basic"></a>Passo a passo: Criando objetos COM o Visual Basic
Ao criar novos aplicativos ou componentes, é melhor criar assemblies do .NET Framework. No entanto, Visual Basic também torna mais fácil para expor um componente do .NET Framework para COM. Isso permite que você forneça novos componentes anteriores aplicativo conjuntos que requerem componentes COM. Este passo a passo demonstra como usar o Visual Basic para expor [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] objetos como objetos COM, com e sem o modelo de classe COM.  
  
 É a maneira mais fácil expor objetos COM usando o modelo de classe COM. O modelo de classe COM cria uma nova classe e, em seguida, configura seu projeto para gerar a camada de interoperabilidade e a classe como um objeto COM e registrá-lo com o sistema operacional.  
  
> [!NOTE]
>  Embora você também pode expor uma classe criada no Visual Basic como um objeto COM para código não gerenciado usar, ele não é um objeto COM real e não pode ser usado pelo Visual Basic. Para obter mais informações, consulte [interoperabilidade COM em aplicativos do .NET Framework](../../../visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications.md).  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-create-a-com-object-by-using-the-com-class-template"></a>Para criar um objeto COM usando o modelo de classe COM  
  
1. Abra um novo projeto de aplicativo do Windows a partir de **arquivo** menu clicando **novo projeto**.  
  
2. No **novo projeto** caixa de diálogo da **tipos de projeto** campo, verifique se o Windows está selecionada. Selecione **biblioteca de classes** da **modelos** e, em seguida, clique **Okey**. O novo projeto é exibido.  
  
3. Selecione **Adicionar Novo Item** da **projeto** menu. A caixa de diálogo **Adicionar Novo Item** é exibida.  
  
4. Selecione **COM Class** da **modelos** e, em seguida, clique **adicionar**. Visual Basic adiciona uma nova classe e configura o novo projeto para interoperabilidade COM.  
  
5. Adicione código como propriedades, métodos e eventos para a classe COM.  
  
6. Selecione **criar ClassLibrary1** da **Build** menu. Visual Basic cria o assembly e registra o objeto COM o sistema operacional.  
  
## <a name="creating-com-objects-without-the-com-class-template"></a>Criando objetos sem o modelo COM Class  
 Você também pode criar uma classe COM manualmente, em vez de usar o modelo de classe COM. Esse procedimento é útil quando você estiver trabalhando na linha de comando ou quando você quiser mais controle sobre como os objetos COM são definidos.  
  
#### <a name="to-set-up-your-project-to-generate-a-com-object"></a>Para configurar seu projeto para gerar um objeto COM  
  
1. Abra um novo projeto de aplicativo do Windows a partir de **arquivo** menu clicando **NewProject**.  
  
2. No **novo projeto** caixa de diálogo da **tipos de projeto** campo, verifique se o Windows está selecionada. Selecione **biblioteca de classes** da **modelos** e, em seguida, clique **Okey**. O novo projeto é exibido.  
  
3. No **Gerenciador de Soluções**, clique com o botão direito do mouse no nó do seu projeto e clique em **Propriedades**. O **Designer de projeto** é exibida.  
  
4. Clique na guia **Compilar**.  
  
5. Selecione o **registrar para interoperabilidade COM** caixa de seleção.  
  
#### <a name="to-set-up-the-code-in-your-class-to-create-a-com-object"></a>Para configurar o código em sua classe para criar um objeto COM  
  
1. Na **Gerenciador de soluções**, clique duas vezes em **Class1.vb** para exibir seu código.  
  
2. Renomeie a classe para `ComClass1`.  
  
3. Adicione as seguintes constantes para `ComClass1`. Eles armazenará as constantes de identificador globalmente exclusivo (GUID) que os objetos COM são necessários para ter.  
  
     [!code-vb[VbVbalrInterop#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#2)]  
  
4. No menu **Ferramentas**, clique em **Criar GUID**. Na caixa de diálogo **Criar GUID**, clique em **Formato do Registro** e clique em **Copiar**. Clique em **Sair**.  
  
5. Substitua a cadeia de caracteres vazia para o `ClassId` com o GUID, removendo à esquerda e à direita de chaves. Por exemplo, se o GUID fornecido pelo Guidgen é `"{2C8B0AEE-02C9-486e-B809-C780A11530FE}"` e em seguida, seu código deve aparecer da seguinte maneira.  
  
     [!code-vb[VbVbalrInterop#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#3)]  
  
6. Repita as etapas anteriores para o `InterfaceId` e `EventsId` constantes, como no exemplo a seguir.  
  
     [!code-vb[VbVbalrInterop#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#4)]  
  
    > [!NOTE]
    >  Certifique-se de que os GUIDs são novos e exclusivos; Caso contrário, o componente COM poderia entrar em conflito com outros componentes COM.  
  
7. Adicione a `ComClass` atributo `ComClass1`, especificando os GUIDs para a ID de classe, a ID de Interface e a ID de eventos, como no exemplo a seguir:  
  
     [!code-vb[VbVbalrInterop#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#5)]  
  
8. Classes COM devem ter um sem parâmetros `Public Sub New()` construtor, ou a classe não registrará corretamente. Adicione um construtor sem parâmetros à classe:  
  
     [!code-vb[VbVbalrInterop#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#6)]  
  
9. Adicione propriedades, métodos e eventos à classe, terminando com um `End Class` instrução. Selecione **compilar solução** da **Build** menu. Visual Basic cria o assembly e registra o objeto COM o sistema operacional.  
  
    > [!NOTE]
    >  Os objetos COM que gerar com o Visual Basic não podem ser usados por outros aplicativos do Visual Basic, porque eles não são objetos de COM true. Tenta adicionar referências a esses objetos COM irá gerar um erro. Para obter detalhes, consulte [interoperabilidade COM em aplicativos do .NET Framework](../../../visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications.md).  
  
## <a name="see-also"></a>Consulte também

- <xref:Microsoft.VisualBasic.ComClassAttribute>
- [Interoperabilidade COM](../../../visual-basic/programming-guide/com-interop/index.md)
- [Passo a passo: implementação de herança com objetos COM](../../../visual-basic/programming-guide/com-interop/walkthrough-implementing-inheritance-with-com-objects.md)
- [Diretiva #Region](../../../visual-basic/language-reference/directives/region-directive.md)
- [Interoperabilidade COM em Aplicativos .NET Framework](../../../visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications.md)
- [Solução de problemas de Interoperabilidade](../../../visual-basic/programming-guide/com-interop/troubleshooting-interoperability.md)
