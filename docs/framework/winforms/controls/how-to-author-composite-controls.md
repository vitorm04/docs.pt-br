---
title: Como criar controles compostos
ms.date: 03/30/2017
helpviewer_keywords:
- UserControl class [Windows Forms], creating composite controls
- user controls [Windows Forms], creating
- user controls [Windows Forms], inheriting from
- composite controls [Windows Forms], creating
ms.assetid: 79c9cf05-5ab6-4a18-886d-88a64748b098
ms.openlocfilehash: 2c7d2c94c376b671d6e9e4e4b71bc8a9b0fbc343
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/05/2018
ms.locfileid: "43731320"
---
# <a name="how-to-author-composite-controls"></a>Como criar controles compostos
Os controles de composição podem ser usados de várias maneiras. É possível criá-los como parte de um projeto de aplicativo da área de trabalho do Windows e usá-los somente em formulários do projeto. Também é possível criá-los em um projeto da Biblioteca de Controles do Windows, compilar o projeto em um assembly e usar os controles em outros projetos. É possível até mesmo herdar deles e usar a herança visual para personalizá-los rapidamente para fins especiais.  
  
> [!NOTE]
>  Caso queira criar um controle de composição para usar no Web Forms, consulte [Desenvolvendo Controles de Servidores ASP.NET Personalizados](https://msdn.microsoft.com/library/fbe26c16-cff4-4089-b3dd-877411f0c0ef).  
>   
>  As caixas de diálogo e os comandos de menu que você vê podem ser diferentes dos descritos na Ajuda, dependendo da sua edição ou das configurações ativas. Para alterar as configurações, escolha **Importar e Exportar Configurações** no menu **Ferramentas**. Para obter mais informações, confira [Personalizar o IDE do Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).  
  
### <a name="to-author-a-composite-control"></a>Criar um controle de composição  
  
1.  Abra um novo projeto de **Aplicativos do Windows** chamado `DemoControlHost`.  
  
2.  No menu **Projeto**, clique em **Adicionar Controle de Usuário**.  
  
3.  Na caixa de diálogo **Adicionar Novo Item**, dê ao arquivo de classe (arquivo .vb ou .cs) o nome que você deseja que o controle de composição tenha.  
  
4.  Clique no botão **Adicionar** para criar o arquivo de classe para o controle de composição.  
  
5.  Adicione os controles da **Caixa de Ferramentas** à superfície do controle de composição.  
  
6.  Coloque o código em procedimentos de evento, a fim de manipular eventos gerados pelo controle de composição ou por seus controles constituintes.  
  
7.  Feche o designer do controle de composição e salve o arquivo quando solicitado.  
  
8.  No menu **Compilar**, clique em **Compilar Solução**.  
  
     O projeto deve ser criado para que os controles personalizados apareçam na **Caixa de Ferramentas**.  
  
9. Use a guia **DemoControlHost** da **Caixa de Ferramentas** para adicionar instâncias do controle ao `Form1`.  
  
### <a name="to-author-a-control-class-library"></a>Criar uma biblioteca de classes de controle  
  
1.  Abra um novo projeto da **Biblioteca de Controles do Windows**.  
  
     Por padrão, o projeto contém um controle de composição.  
  
2.  Adicione controles e código, conforme descrito no procedimento acima.  
  
3.  Escolha um controle que as classes de herança não alterarão e defina a propriedade **Modificadores** desse controle como **Privada**.  
  
4.  Compile a DLL.  
  
### <a name="to-inherit-from-a-composite-control-in-a-control-class-library"></a>Herdar de um controle de composição em uma biblioteca de classes de controle  
  
1.  No menu **Arquivo**, aponte para **Adicionar** e selecione **Novo Projeto** para adicionar um novo projeto dos **Aplicativos do Windows** à solução.  
  
2.  No **Gerenciador de Soluções**, clique com o botão direito do mouse na pasta **Referências** do novo projeto e escolha **Adicionar Referência** para abrir a caixa de diálogo **Adicionar Referência**.  
  
3.  Selecione a guia **Projetos** e clique duas vezes no projete de biblioteca de controle.  
  
4.  No menu **Compilar**, clique em **Compilar Solução**.  
  
5.  No **Gerenciador de Soluções**, clique com o botão direito do mouse no projeto de biblioteca de controle e selecione **Adicionar Novo Item** no menu de atalho.  
  
6.  Selecione o modelo **Controle de Usuário Herdado** na caixa de diálogo **Adicionar Novo Item**.  
  
7.  Na caixa de diálogo **Selecionador de Herança**, clique duas vezes no controle do qual você deseja herdar.  
  
     Um novo controle será adicionado ao projeto.  
  
8.  Abra o designer visual do novo controle e adicione outros controles constituintes.  
  
     É possível ver os controles constituintes que foram herdados do controle composição na DLL e alterar as propriedades de controles cuja propriedade **Modificadores** for **Pública**. Não é possível alterar as propriedades do controle cuja propriedade **Modificadores** for **Privada**.  
  
## <a name="see-also"></a>Consulte também  
 [Passo a passo: criando um controle de composição com o Visual Basic](../../../../docs/framework/winforms/controls/walkthrough-authoring-a-composite-control-with-visual-basic.md)  
 [Passo a passo: criando um controle de composição com o Visual C#](../../../../docs/framework/winforms/controls/walkthrough-authoring-a-composite-control-with-visual-csharp.md)  
 [Passo a passo: herdando um controle dos Windows Forms com Visual Basic](../../../../docs/framework/winforms/controls/walkthrough-inheriting-from-a-windows-forms-control-with-visual-basic.md)  
 [Passo a passo: herdando um controle dos Windows Forms com Visual C#](../../../../docs/framework/winforms/controls/walkthrough-inheriting-from-a-windows-forms-control-with-visual-csharp.md)  
 [Recomendações do Tipo de Controle](../../../../docs/framework/winforms/controls/control-type-recommendations.md)  
 [Como Criar Controles para o Windows Forms](../../../../docs/framework/winforms/controls/how-to-author-controls-for-windows-forms.md)  
 [Variedades de controles personalizados](../../../../docs/framework/winforms/controls/varieties-of-custom-controls.md)
