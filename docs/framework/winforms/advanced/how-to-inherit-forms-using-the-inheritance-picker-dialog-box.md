---
title: Como herdar formulários usando a caixa de diálogo Selecionador de Herança
ms.date: 03/30/2017
helpviewer_keywords:
- inheritance [Windows Forms], forms
- Inheritance Picker dialog box
- inherited forms [Windows Forms], creating
ms.assetid: 969b4c04-12aa-4297-93a2-0ae747447823
ms.openlocfilehash: 7a6de60ec7621792b4f19857a2743f64cbdc686c
ms.sourcegitcommit: 586dbdcaef9767642436b1e4efbe88fb15473d6f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/06/2018
ms.locfileid: "48837291"
---
# <a name="how-to-inherit-forms-using-the-inheritance-picker-dialog-box"></a>Como herdar formulários usando a caixa de diálogo Selecionador de Herança
A maneira mais fácil de herdar um formulário ou outro objeto é usar a caixa de diálogo **Selecionador de Herança**. Com ela, você pode aproveitar códigos ou interfaces do usuário já criados em outras soluções.  
  
> [!NOTE]
>  Para herdar de um formulário com a caixa de diálogo **Selecionador de Herança**, o projeto que contém esse formulário deve ter sido incluído em um arquivo executável ou DLL. Para compilar o projeto, escolha **Compilar Solução** no menu **Compilar**.  
>   
>  As caixas de diálogo e os comandos de menu que você vê podem ser diferentes dos descritos na Ajuda, dependendo da sua edição ou das configurações ativas. Para alterar as configurações, escolha **Importar e Exportar Configurações** no menu **Ferramentas**. Para obter mais informações, confira [Personalizar o IDE do Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).  
  
### <a name="to-create-a-windows-form-inherited-from-an-existing-form-by-using-the-inheritance-picker"></a>Para criar um Formulário do Windows herdado de um formulário existente usando o seletor de herança  
  
1.  No menu **Projeto**, escolha **Adicionar Formulário do Windows**.  
  
     A caixa de diálogo **Adicionar Novo Item** é aberta.  
  
2.  Pesquisa o **formulário herdado** modelo a partir da caixa de pesquisa ou clicando na **Windows Forms** categoria, selecione-o e nomeie-o na **nome** caixa. Clique no botão **Adicionar** para continuar.  
  
     A caixa de diálogo **Selecionador de Herança** é aberta. Se o projeto atual já contiver formulários, eles serão exibidos na caixa de diálogo **Selecionador de Herança**.  
  
3.  Para herdar de um formulário em outro assembly, clique no botão **Procurar**.  
  
4.  Dentro da caixa de diálogo **Selecionar um arquivo que contenha um componente do qual herdar**, navegue para o projeto que contém o formulário ou módulo desejado.  
  
5.  Clique no nome do arquivo .dll ou .exe para selecioná-la e clique no botão **Abrir**.  
  
     Isso o leva de volta à caixa de diálogo **Selecionador de Herança**, na qual o componente agora está listado, junto com o projeto no qual ele está localizado.  
  
6.  Selecione o componente.  
  
     No **Gerenciador de Soluções**, o componente é adicionado ao seu projeto. Se ela tiver uma interface do usuário, controles que fazem parte do formulário herdado serão marcados com um glifo (![captura de tela VisualBasicInheritanceSymbol](../../../../docs/framework/winforms/advanced/media/vbinheritanceglyph.gif "vbInheritanceGlyph")) e, quando selecionados, terão uma borda indicando o nível de segurança que o controle tem sobre o formulário da superclasse. Os comportamentos que correspondem aos diferentes níveis de segurança são listados na tabela a seguir.  
  
    |Nível de segurança de controle|Interação disponível por meio do Designer e do Editor de Códigos com Formulário Herdado|  
    |-------------------------------|--------------------------------------------------------------------------------|  
    |Público|Borda padrão com alças de dimensionamento: o controle pode ser dimensionado e movido. O controle pode ser acessado internamente pela classe que o declara e externamente por outras classes.|  
    |Protegido|Borda padrão com alças de dimensionamento: o controle pode ser dimensionado e movido. Pode ser acessado internamente pela classe que o declara e qualquer classe que herda da classe pai, mas não pode ser acessado por classes externas.|  
    |Protegido Interno (Amigo Protegido, no Visual Basic)|Borda padrão com alças de dimensionamento: o controle pode ser dimensionado e movido. Pode ser acessado internamente pela classe que o declara, por qualquer classe que herde da classe pai e por outros membros do assembly que o contém.|  
    |Interno (Amigo, no Visual Basic)|Borda padrão sem alça de dimensionamento, mostrada no formulário, propriedades visíveis na janela **Propriedades**. No entanto, todos os aspectos do controle serão considerados somente leitura. Você não pode mover nem dimensionar o controle nem alterar suas propriedades. Se o controle for um recipiente de outros controles, como uma caixa de grupo, novos controles não poderão ser adicionados e os controles existentes não poderão ser removidos, mesmo que os controles sejam públicos. O controle só pode ser acessado por outros membros do assembly que o contém.|  
    |Particular|Borda padrão sem alça de dimensionamento, mostrada no formulário, propriedades visíveis na janela **Propriedades**. No entanto, todos os aspectos do controle serão considerados somente leitura. Você não pode mover nem dimensionar o controle nem alterar suas propriedades. Se o controle for um recipiente de outros controles, como uma caixa de grupo, novos controles não poderão ser adicionados e os controles existentes não poderão ser removidos, mesmo que os controles sejam públicos. O controle só pode ser acessado pela classe que o declara.|  
  
     Para obter informações sobre como alterar a aparência do formulário de base, consulte [Efeitos da modificação da aparência de um formulário de base](../../../../docs/framework/winforms/advanced/effects-of-modifying-base-form-appearance.md).  
  
    > [!NOTE]
    >  Ao combinar controles e componentes herdados com controles e componentes padrão no Windows Forms, você pode encontrar conflitos com a ordenação z. Você pode corrigir isso modificando a ordenação z, o que é feito clicando no menu **Formato**, apontando para **Ordem** e, em seguida, clicando em **Trazer para Frente** ou **Enviar para Trás**. Para obter mais informações sobre a ordem z de controles, consulte [Como dispor em camadas objetos no Windows Forms](../../../../docs/framework/winforms/controls/how-to-layer-objects-on-windows-forms.md).  
  
## <a name="see-also"></a>Consulte também  
 [Instrução Inherits](~/docs/visual-basic/language-reference/statements/inherits-statement.md)  
 [using](~/docs/csharp/language-reference/keywords/using.md)  
 [Efeitos da Modificação da Aparência de um Formulário Base](../../../../docs/framework/winforms/advanced/effects-of-modifying-base-form-appearance.md)  
 [Herança Visual dos Windows Forms](../../../../docs/framework/winforms/advanced/windows-forms-visual-inheritance.md)
