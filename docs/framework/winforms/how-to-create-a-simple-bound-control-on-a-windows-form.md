---
title: 'Como: criar um controle associado simples em um Windows Form'
ms.date: 03/30/2017
helpviewer_keywords:
- data binding [Windows Forms], simple data binding
- Windows Forms controls, data binding
ms.assetid: 3bcaded8-0f1a-4cc0-8830-f59be253bf4e
ms.openlocfilehash: fc59e6d5e71bfc69dea0bfc5098a1fa14c97d4b6
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62008948"
---
# <a name="how-to-create-a-simple-bound-control-on-a-windows-form"></a>Como: criar um controle associado simples em um Windows Form
Com a *associação simples*, é possível exibir um elemento de dados simples, como um valor de coluna de uma tabela de dados em um controle. Você pode associar de maneira simples qualquer propriedade de um controle a um valor de dados.  
  
> [!NOTE]
>  As caixas de diálogo e os comandos de menu que você vê podem ser diferentes dos descritos na Ajuda, dependendo da sua edição ou das configurações ativas. Para alterar as configurações, escolha **Importar e Exportar Configurações** no menu **Ferramentas**. Para obter mais informações, confira [Personalizar o IDE do Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).  
  
### <a name="to-simple-bind-a-control"></a>Para associar de maneira simples um controle  
  
1. Conecte-se a uma fonte de dados. Para obter mais informações, consulte [Conectando a uma fonte de dados](../data/adonet/connecting-to-a-data-source.md).  
  
2. No formulário, selecione o controle e abra exiba janela **Propriedades**.  
  
3. Expanda a propriedade **(DataBindings)**.  
  
     As propriedades geralmente mais associadas são exibidas sob a propriedade **(DataBindings)**. Por exemplo, na maioria dos controles, a propriedade **Text** é vinculada com mais frequência.  
  
4. Se a propriedade que deseja associar não for uma das propriedades comumente vinculadas, clique no botão **Elipse** (![VisualStudioEllipsesButton screenshot](./media/vbellipsesbutton.png "vbEllipsesButton")) na caixa **(Avançado)** para exibir a caixa de diálogo **Formatação e associação avançada** com uma lista completa de propriedades para esse controle.  
  
5. Selecione a propriedade que deseja associar e clique na seta suspensa em **Associação**.  
  
     Uma lista de fontes de dados disponíveis é exibida.  
  
6. Expanda a fonte de dados a que deseja associar até encontrar o elemento de dados individual desejado. Por exemplo, se você estiver associando a um valor de coluna na tabela do conjunto de dados, expanda o nome do conjunto de dados e o nome da tabela para exibir os nomes das colunas.  
  
7. Clique no nome de um elemento que receberá a associação.  
  
8. Se você estiver trabalhando na caixa de diálogo **Formatação e associação avançada**, clique em **OK** para voltar para a janela **Propriedades**.  
  
9. Se deseja associar propriedades adicionais do controle, repita as etapas 3 a 7.  
  
    > [!NOTE]
    >  Como controles de associação simples mostram apenas um elemento de dados, é muito comum incluir a lógica de navegação em um Windows Form com controles de associação simples.  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Forms.Binding>
- [Associação de dados do Windows Forms](windows-forms-data-binding.md)
- [Vinculação de dados e os Windows Forms](data-binding-and-windows-forms.md)
