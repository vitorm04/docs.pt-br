---
title: 'Passo a passo: Criando objetos com com Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- COM interop [Visual Basic], creating COM objects
- COM objects, creating
- COM interop [Visual Basic], walkthroughs
- object creation [Visual Basic], COM objects
- COM objects, walkthroughs
ms.assetid: 7b07a463-bc72-4392-9ba0-9dfcb697a44f
ms.openlocfilehash: 39012ebdd8946f707fe459cb09bb2bbfc8e50088
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69958276"
---
# <a name="walkthrough-creating-com-objects-with-visual-basic"></a>Passo a passo: Criando objetos com com Visual Basic
Ao criar novos aplicativos ou componentes, é melhor criar assemblies de .NET Framework. No entanto, Visual Basic também facilita a exposição de um componente de .NET Framework para COM. Isso permite que você forneça novos componentes para conjuntos de aplicativos anteriores que exigem componentes COM. Este tutorial demonstra como usar Visual Basic para expor .NET Framework objetos como objetos COM, com e sem o modelo de classe COM.  
  
 A maneira mais fácil de expor objetos COM é usando o modelo de classe COM. O modelo de classe COM cria uma nova classe e, em seguida, configura seu projeto para gerar a classe e a camada de interoperabilidade como um objeto COM e registrá-lo no sistema operacional.  
  
> [!NOTE]
> Embora você também possa expor uma classe criada em Visual Basic como um objeto COM para que o código não gerenciado use, ele não é um objeto COM verdadeiro e não pode ser usado por Visual Basic. Para obter mais informações, consulte interoperabilidade [com em aplicativos .NET Framework](../../../visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications.md).  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-create-a-com-object-by-using-the-com-class-template"></a>Para criar um objeto COM usando o modelo de classe COM  
  
1. Abra um novo projeto de aplicativo do Windows no menu **arquivo** clicando em **novo projeto**.  
  
2. Na caixa de diálogo **novo projeto** , no campo **tipos de projeto** , verifique se Windows está selecionado. Selecione **biblioteca de classes** na lista **modelos** e clique em **OK**. O novo projeto é exibido.  
  
3. Selecione **Adicionar novo item** no menu **projeto** . A caixa de diálogo **Adicionar Novo Item** é exibida.  
  
4. Selecione a **classe com** na lista **modelos** e clique em **Adicionar**. Visual Basic adiciona uma nova classe e configura o novo projeto para interoperabilidade COM.  
  
5. Adicione um código como propriedades, métodos e eventos à classe COM.  
  
6. Selecione **criar ClassLibrary1** no menu **Compilar** . Visual Basic compila o assembly e registra o objeto com com o sistema operacional.  
  
## <a name="creating-com-objects-without-the-com-class-template"></a>Criando objetos COM sem o modelo de classe COM  
 Você também pode criar uma classe COM manualmente em vez de usar o modelo de classe COM. Esse procedimento é útil quando você está trabalhando na linha de comando ou quando deseja obter mais controle sobre como os objetos COM são definidos.  
  
#### <a name="to-set-up-your-project-to-generate-a-com-object"></a>Para configurar seu projeto para gerar um objeto COM  
  
1. Abra um novo projeto de aplicativo do Windows no menu **arquivo** clicando em **NewProject**.  
  
2. Na caixa de diálogo **novo projeto** , no campo **tipos de projeto** , verifique se Windows está selecionado. Selecione **biblioteca de classes** na lista **modelos** e clique em **OK**. O novo projeto é exibido.  
  
3. No **Gerenciador de Soluções**, clique com o botão direito do mouse no nó do seu projeto e clique em **Propriedades**. O **Designer de projeto** é exibido.  
  
4. Clique na guia **Compilar**.  
  
5. Marque a caixa de seleção **registrar para interoperabilidade com** .  
  
#### <a name="to-set-up-the-code-in-your-class-to-create-a-com-object"></a>Para configurar o código em sua classe para criar um objeto COM  
  
1. Em **Gerenciador de soluções**, clique duas vezes em **Class1. vb** para exibir seu código.  
  
2. Renomeie a `ComClass1`classe como.  
  
3. Adicione as constantes a seguir `ComClass1`a. Eles armazenarão as constantes GUID (identificador global exclusivo) que os objetos COM devem ter.  
  
     [!code-vb[VbVbalrInterop#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#2)]  
  
4. No menu **Ferramentas**, clique em **Criar GUID**. Na caixa de diálogo **Criar GUID**, clique em **Formato do Registro** e clique em **Copiar**. Clique em **Sair**.  
  
5. Substitua a cadeia de caracteres `ClassId` vazia do pelo GUID, removendo as chaves à esquerda e à direita. Por exemplo, se o GUID fornecido pelo Guidgen for `"{2C8B0AEE-02C9-486e-B809-C780A11530FE}"` , seu código deverá aparecer da seguinte maneira.  
  
     [!code-vb[VbVbalrInterop#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#3)]  
  
6. Repita as etapas anteriores para as `InterfaceId` constantes `EventsId` e, como no exemplo a seguir.  
  
     [!code-vb[VbVbalrInterop#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#4)]  
  
    > [!NOTE]
    > Certifique-se de que os GUIDs são novos e exclusivos; caso contrário, o componente COM pode entrar em conflito com outros componentes COM.  
  
7. Adicione o `ComClass` atributo a `ComClass1`, especificando os GUIDs para a ID de classe, ID de interface e ID de eventos, como no exemplo a seguir:  
  
     [!code-vb[VbVbalrInterop#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#5)]  
  
8. As classes com devem ter um `Public Sub New()` Construtor sem parâmetros ou a classe não será registrada corretamente. Adicione um construtor sem parâmetros à classe:  
  
     [!code-vb[VbVbalrInterop#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#6)]  
  
9. Adicione Propriedades, métodos e eventos à classe, encerrando-o com uma `End Class` instrução. Selecione **Compilar solução** no menu **Compilar** . Visual Basic compila o assembly e registra o objeto com com o sistema operacional.  
  
    > [!NOTE]
    > Os objetos COM que você gera com Visual Basic não podem ser usados por outros aplicativos Visual Basic porque não são objetos COM verdadeiros. As tentativas de adicionar referências a esses objetos COM gerarão um erro. Para obter detalhes, consulte interoperabilidade [com em aplicativos .NET Framework](../../../visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications.md).  
  
## <a name="see-also"></a>Consulte também

- <xref:Microsoft.VisualBasic.ComClassAttribute>
- [Interoperabilidade COM](../../../visual-basic/programming-guide/com-interop/index.md)
- [Passo a passo: implementação de herança com objetos COM](../../../visual-basic/programming-guide/com-interop/walkthrough-implementing-inheritance-with-com-objects.md)
- [Diretiva #Region](../../../visual-basic/language-reference/directives/region-directive.md)
- [Interoperabilidade COM em Aplicativos .NET Framework](../../../visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications.md)
- [Solução de problemas de Interoperabilidade](../../../visual-basic/programming-guide/com-interop/troubleshooting-interoperability.md)
