---
title: Visão geral do componente ErrorProvider
ms.date: 03/30/2017
f1_keywords:
- ErrorProvider
helpviewer_keywords:
- errors [Windows Forms], displaying to users
- error messages [Windows Forms], displaying
- ErrorProvider component [Windows Forms], about ErrorProvider component
ms.assetid: ced189f2-b5c8-46a7-a6f1-37f5af95dc99
ms.openlocfilehash: b66e97d97d0d8c2ea4e9bdba29f8ff35e486e1f6
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76745796"
---
# <a name="errorprovider-component-overview-windows-forms"></a>Visão geral do componente ErrorProvider (Windows Forms)
O componente [ErrorProvider](errorprovider-component-windows-forms.md) dos Windows Forms é usado para validar a entrada do usuário em um formulário ou controle. Ele é normalmente usado junto com a validação de entrada do usuário em um formulário ou para exibir erros dentro de um conjunto de dados. Um provedor de erro é uma alternativa melhor que exibir uma mensagem de erro em uma caixa de mensagem, pois depois que uma caixa de mensagem for descartada, a mensagem de erro não estará mais visível. O componente <xref:System.Windows.Forms.ErrorProvider> exibe um ícone de erro (![um ponto de exclamação branco dentro de um círculo vermelho.](./media/errorprovider-component-overview-windows-forms/vb-error-provider-icon.gif)) ao lado do controle relevante, como uma caixa de texto; Quando o usuário posiciona o ponteiro do mouse sobre o ícone de erro, uma dica de ferramenta é exibida, mostrando a cadeia de caracteres de mensagem de erro.  
  
## <a name="key-properties"></a>Propriedades da chave  
 As propriedades de chave do componente de <xref:System.Windows.Forms.ErrorProvider> são <xref:System.Windows.Forms.ErrorProvider.DataSource%2A>, <xref:System.Windows.Forms.ErrorProvider.ContainerControl%2A>e <xref:System.Windows.Forms.ErrorProvider.Icon%2A>. Ao usar <xref:System.Windows.Forms.ErrorProvider> componente com controles vinculados a dados, a propriedade <xref:System.Windows.Forms.ErrorProvider.ContainerControl%2A> deve ser definida como o contêiner apropriado (geralmente o Windows Form) para que o componente exiba um ícone de erro no formulário. Quando o componente é adicionado no designer, a propriedade <xref:System.Windows.Forms.ErrorProvider.ContainerControl%2A> é definida como a forma que a contém; Se você adicionar o controle no código, deverá defini-lo por conta própria.  
  
 A propriedade <xref:System.Windows.Forms.ErrorProvider.Icon%2A> pode ser definida como um ícone de erro personalizado em vez do padrão. Quando a propriedade <xref:System.Windows.Forms.ErrorProvider.DataSource%2A> é definida, o componente <xref:System.Windows.Forms.ErrorProvider> pode exibir mensagens de erro para um conjunto de um DataSet. O método de chave do componente <xref:System.Windows.Forms.ErrorProvider> é o método <xref:System.Windows.Forms.ErrorProvider.SetError%2A>, que especifica a cadeia de caracteres de mensagem de erro e onde o ícone de erro deve aparecer.  
  
> [!NOTE]
> O componente <xref:System.Windows.Forms.ErrorProvider> não fornece suporte interno para clientes de acessibilidade. Para tornar seu aplicativo acessível ao usar esse componente, você deve fornecer um mecanismo de comentários acessível adicional.  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Forms.ErrorProvider>
- [Como exibir erros dentro de um DataSet com o componente ErrorProvider dos Windows Forms](view-errors-within-a-dataset-with-wf-errorprovider-component.md)
- [Como exibir ícones de erro para validação do formulário com o componente ErrorProvider dos Windows Forms](display-error-icons-for-form-validation-with-wf-errorprovider.md)
