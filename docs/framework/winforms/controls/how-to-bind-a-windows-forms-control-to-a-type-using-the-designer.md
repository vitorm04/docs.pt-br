---
title: Associar o controle a um tipo usando o designer
ms.date: 03/30/2017
helpviewer_keywords:
- controls [Windows Forms], binding to a type
- BindingSource component [Windows Forms], binding to a type
- types [Windows Forms], binding controls to
ms.assetid: 5ab984b5-c2d0-4638-a572-1c84013e8746
ms.openlocfilehash: 2257489e123ceeea819ad3538952db51b726c7e5
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76742022"
---
# <a name="how-to-bind-a-windows-forms-control-to-a-type-using-the-designer"></a>Como associar um controle dos Windows Forms a um tipo usando o designer

Quando estiver compilando controles que interagem com os dados, pode ser necessário associar um controle a um tipo, em vez de um objeto. Geralmente é necessário associar um controle a um tipo no tempo de design, quando os dados podem não estar disponíveis, mas ainda é recomendável fazer com que os controles associados a dados exibam dados da interface pública de um tipo. Os procedimentos a seguir demonstram como criar um novo <xref:System.Windows.Forms.BindingSource> associado a um tipo e como associar uma das propriedades do tipo à propriedade <xref:System.Windows.Forms.TextBox.Text%2A> de um <xref:System.Windows.Forms.TextBox>.

### <a name="to-bind-the-bindingsource-to-a-type"></a>Associar o BindingSource a um tipo

1. Criar um projeto de Windows Forms **(arquivo** > **novo** **projeto** de >  > **Visual C#**  ou **Visual Basic** > área de **trabalho clássica** > Windows Forms **aplicativo**).

2. No modo **design** , arraste um componente <xref:System.Windows.Forms.BindingSource> para o formulário.

3. Na janela **Propriedades** , clique na seta da propriedade <xref:System.Windows.Forms.BindingSource.DataSource%2A>.

4. No **Editor de tipo de interface do usuário de DataSource**, clique em **Adicionar fonte de dados do projeto**.

5. Na página **Escolher um tipo de fonte de dados**, selecione **Objeto** e clique em **Avançar**.

6. Selecione o tipo para associar a:

    - Se o tipo ao qual você deseja associar está no projeto atual ou o assembly que contém o tipo já foi adicionado como uma referência, expanda os nós para localizar o tipo desejado e, em seguida, selecione-o.

      \-ou-

    - Se o tipo ao qual você deseja associar estiver em outro assembly, não atualmente na lista de referências, clique em **Adicionar referência**e, em seguida, clique na guia **projetos** . Selecione o projeto que contém o objeto comercial desejado e clique em **OK**. Este projeto será exibido na lista de assemblies, portanto é possível expandir os nós para encontrar o tipo desejado e, em seguida, selecioná-lo.

      > [!NOTE]
      > Se você desejar associar a um tipo em uma estrutura ou assembly Microsoft, desmarque a caixa de seleção **Ocultar assemblies que começam com Microsoft ou System**.

7. Clique em **Avançar**e em **Concluir**.

### <a name="to-bind-the-control-to-the-bindingsource"></a>Associar o controle ao BindingSource

1. Adicione um <xref:System.Windows.Forms.TextBox> ao formulário.

2. Na janela **Propriedades**, expanda o nó **(DataBindings)** .

3. Clique na seta ao lado da propriedade <xref:System.Windows.Forms.TextBox.Text%2A>.

4. No **Editor de tipo de interface do usuário do DataSource**, expanda o nó para o <xref:System.Windows.Forms.BindingSource> adicionado anteriormente e selecione a propriedade do tipo vinculado que você deseja associar à propriedade <xref:System.Windows.Forms.TextBox.Text%2A> da <xref:System.Windows.Forms.TextBox>.

## <a name="see-also"></a>Veja também

- [Componente BindingSource](bindingsource-component.md)
- [Como associar um controle do Windows Forms a um tipo](how-to-bind-a-windows-forms-control-to-a-type.md)
- [Associar controles a dados no Visual Studio](/visualstudio/data-tools/bind-controls-to-data-in-visual-studio)
