---
title: 'Como: criar um controle associado e formatar os dados exibidos'
ms.date: 03/30/2017
helpviewer_keywords:
- data [Windows Forms], formatting
- bound controls [Windows Forms], creating
- bound controls [Windows Forms], formatting data
ms.assetid: d5a56228-899d-41d9-8af8-87b3f4ec2f94
ms.openlocfilehash: b5ad85a9477ca32cd28f246abe4ece3cace43182
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/21/2019
ms.locfileid: "69666778"
---
# <a name="how-to-create-a-bound-control-and-format-the-displayed-data"></a>Como: criar um controle associado e formatar os dados exibidos

Com a associação de dados do Windows Forms, você pode formatar os dados exibidos em um controle associado a dados usando a caixa de diálogo **Formatação e associação avançada**.

### <a name="to-bind-a-control-and-format-the-displayed-data"></a>Associar um controle e formatar os dados exibidos

1. Conecte-se a uma fonte de dados.

     Para obter mais informações, consulte [Conectando a uma fonte de dados](../data/adonet/connecting-to-a-data-source.md).

2. No formulário, selecione o controle e abra a janela Propriedades.

3. Expanda a propriedade **(DataBindings)** e, em seguida, na caixa **(avançado)** , clique no botão![de reticências (o botão de reticências (...) na](./media/how-to-create-a-bound-control-and-format-the-displayed-data/visual-studio-ellipsis-button.png)janela Propriedades do Visual Studio.) para exibir a **formatação e avançado** Caixa de diálogo de associação, que tem uma lista completa de propriedades para esse controle.

4. Selecione a propriedade que você deseja associar e, em seguida, clique na seta **Associação**.

     Uma lista de fontes de dados disponíveis é exibida.

5. Expanda a fonte de dados a que deseja associar até encontrar o elemento de dados individual desejado.

     Por exemplo, se você estiver associando a um valor de coluna na tabela do conjunto de dados, expanda o nome do conjunto de dados e o nome da tabela para exibir os nomes das colunas.

6. Clique no nome de um elemento que receberá a associação.

7. Na caixa **Tipo de formato**, clique no formato que você deseja aplicar aos dados exibidos no controle.

     Em todos os casos, você pode especificar o valor exibido no controle se a fonte de dados <xref:System.DBNull>contiver. Caso contrário, as opções variam um pouco, dependendo do tipo de formato escolhido. A tabela a seguir mostra os tipos e opções de formato.

    |Tipo de formato|Opção de formatação|
    |-----------------|-----------------------|
    |Sem Formatação|Nenhuma opção.|
    |Numeric|Especifique o número de casas decimais usando o controle superior/inferior **Casas decimais**.|
    |Moeda|Especifique o número de casas decimais usando o controle superior/inferior **Casas decimais**.|
    |Date Time|Selecione como a data e a hora devem ser exibidas selecionando um dos itens na caixa de seleção **Tipo**.|
    |Científico|Especifique o número de casas decimais usando o controle superior/inferior **Casas decimais**.|
    |Personalizado|Especifique uma cadeia de caracteres de formato personalizada usando.<br /><br /> Para obter mais informações, consulte [Tipos de formatação](../../standard/base-types/formatting-types.md). **Observação:**  Cadeias de caracteres de formato personalizado não têm garantia de ida e volta com êxito entre a fonte de dados e o controle ligado. Em vez disso <xref:System.Windows.Forms.Binding.Parse> , <xref:System.Windows.Forms.Binding.Format> manipule o evento ou para a associação e aplique a formatação personalizada no código de manipulação de eventos.|

8. Clique em **OK** para fechar a caixa de diálogo **Formatação e associação avançada** e retornar para a janela Propriedades.

## <a name="see-also"></a>Consulte também

- [Como: Criar um controle de associação simples em um formulário do Windows](how-to-create-a-simple-bound-control-on-a-windows-form.md)
- [Validação da entrada do usuário nos Windows Forms](user-input-validation-in-windows-forms.md)
- [Associação de dados do Windows Forms](windows-forms-data-binding.md)
