---
title: Como criar um controle associado e formatar os dados exibidos
ms.date: 03/30/2017
helpviewer_keywords:
- data [Windows Forms], formatting
- bound controls [Windows Forms], creating
- bound controls [Windows Forms], formatting data
ms.assetid: d5a56228-899d-41d9-8af8-87b3f4ec2f94
ms.openlocfilehash: 9055ec9c4b646e0c86819e4e72db8ce20086bace
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33542204"
---
# <a name="how-to-create-a-bound-control-and-format-the-displayed-data"></a>Como criar um controle associado e formatar os dados exibidos
Com a associação de dados do Windows Forms, você pode formatar os dados exibidos em um controle associado a dados usando a caixa de diálogo **Formatação e associação avançada**.  
  
> [!NOTE]
>  As caixas de diálogo e os comandos de menu que você vê podem ser diferentes dos descritos na Ajuda, dependendo da sua edição ou das configurações ativas. Para alterar as configurações, escolha **Importar e Exportar Configurações** no menu **Ferramentas**. Para obter mais informações, consulte [Personalizando configurações de desenvolvimento no Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-bind-a-control-and-format-the-displayed-data"></a>Associar um controle e formatar os dados exibidos  
  
1.  Conecte-se a uma fonte de dados.  
  
     Para obter mais informações, consulte [Conectando a uma fonte de dados](../../../docs/framework/data/adonet/connecting-to-a-data-source.md).  
  
2.  No formulário, selecione o controle e abra a janela Propriedades.  
  
3.  Expanda a propriedade **(DataBindings)** e, na caixa **(Advanced)**, clique no botão de reticências (![captura de tela do VisualStudioEllipsesButton](../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) para exibir a caixa de diálogo **Formatação e associação avançada**, que tem uma lista completa de propriedades do controle.  
  
4.  Selecione a propriedade que você deseja associar e, em seguida, clique na seta **Associação**.  
  
     Uma lista de fontes de dados disponíveis é exibida.  
  
5.  Expanda a fonte de dados a que deseja associar até encontrar o elemento de dados individual desejado.  
  
     Por exemplo, se você estiver associando a um valor de coluna na tabela do conjunto de dados, expanda o nome do conjunto de dados e o nome da tabela para exibir os nomes das colunas.  
  
6.  Clique no nome de um elemento que receberá a associação.  
  
7.  Na caixa **Tipo de formato**, clique no formato que você deseja aplicar aos dados exibidos no controle.  
  
     Em cada caso, você pode especificar o valor exibido no controle se a fonte de dados contém <xref:System.DBNull>. Caso contrário, as opções variam um pouco, dependendo do tipo de formato escolhido. A tabela a seguir mostra os tipos e opções de formato.  
  
    |Tipo de formato|Opção de formatação|  
    |-----------------|-----------------------|  
    |Sem Formatação|Nenhuma opção.|  
    |Numeric|Especifique o número de casas decimais usando o controle superior/inferior **Casas decimais**.|  
    |Moeda|Especifique o número de casas decimais usando o controle superior/inferior **Casas decimais**.|  
    |Date Time|Selecione como a data e a hora devem ser exibidas selecionando um dos itens na caixa de seleção **Tipo**.|  
    |Científico|Especifique o número de casas decimais usando o controle superior/inferior **Casas decimais**.|  
    |Personalizado|Especifique uma cadeia de caracteres de formato personalizada usando.<br /><br /> Para obter mais informações, consulte [Tipos de formatação](../../../docs/standard/base-types/formatting-types.md). **Observação:** não há garantias de que as cadeias de caracteres de formato personalizadas realização a viagem de ida e volta entre a fonte de dados e o controle associado com êxito. Identificar o <xref:System.Windows.Forms.Binding.Parse> ou <xref:System.Windows.Forms.Binding.Format> evento para a associação e aplicar formatação personalizada no código de manipulação de eventos.|  
  
8.  Clique em **OK** para fechar a caixa de diálogo **Formatação e associação avançada** e retornar para a janela Propriedades.  
  
## <a name="see-also"></a>Consulte também  
 [Como criar um controle associado simples em um Windows Form](../../../docs/framework/winforms/how-to-create-a-simple-bound-control-on-a-windows-form.md)  
 [Validação da entrada do usuário nos Windows Forms](../../../docs/framework/winforms/user-input-validation-in-windows-forms.md)  
 [Associação de dados do Windows Forms](../../../docs/framework/winforms/windows-forms-data-binding.md)
