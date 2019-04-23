---
title: 'Como: criar um controle associado simples em um Windows Form'
ms.date: 03/30/2017
helpviewer_keywords:
- data binding [Windows Forms], simple data binding
- Windows Forms controls, data binding
ms.assetid: 3bcaded8-0f1a-4cc0-8830-f59be253bf4e
ms.openlocfilehash: fc59e6d5e71bfc69dea0bfc5098a1fa14c97d4b6
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59322167"
---
# <a name="how-to-create-a-simple-bound-control-on-a-windows-form"></a><span data-ttu-id="d7148-102">Como: criar um controle associado simples em um Windows Form</span><span class="sxs-lookup"><span data-stu-id="d7148-102">How to: Create a Simple-Bound Control on a Windows Form</span></span>
<span data-ttu-id="d7148-103">Com a *associação simples*, é possível exibir um elemento de dados simples, como um valor de coluna de uma tabela de dados em um controle.</span><span class="sxs-lookup"><span data-stu-id="d7148-103">With *simple binding*, you can display a single data element, such as a column value from a dataset table, in a control.</span></span> <span data-ttu-id="d7148-104">Você pode associar de maneira simples qualquer propriedade de um controle a um valor de dados.</span><span class="sxs-lookup"><span data-stu-id="d7148-104">You can simple-bind any property of a control to a data value.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d7148-105">As caixas de diálogo e os comandos de menu que você vê podem ser diferentes dos descritos na Ajuda, dependendo da sua edição ou das configurações ativas.</span><span class="sxs-lookup"><span data-stu-id="d7148-105">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="d7148-106">Para alterar as configurações, escolha **Importar e Exportar Configurações** no menu **Ferramentas**.</span><span class="sxs-lookup"><span data-stu-id="d7148-106">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="d7148-107">Para obter mais informações, confira [Personalizar o IDE do Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).</span><span class="sxs-lookup"><span data-stu-id="d7148-107">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
### <a name="to-simple-bind-a-control"></a><span data-ttu-id="d7148-108">Para associar de maneira simples um controle</span><span class="sxs-lookup"><span data-stu-id="d7148-108">To simple-bind a control</span></span>  
  
1. <span data-ttu-id="d7148-109">Conecte-se a uma fonte de dados.</span><span class="sxs-lookup"><span data-stu-id="d7148-109">Connect to a data source.</span></span> <span data-ttu-id="d7148-110">Para obter mais informações, consulte [Conectando a uma fonte de dados](../data/adonet/connecting-to-a-data-source.md).</span><span class="sxs-lookup"><span data-stu-id="d7148-110">For more information, see [Connecting to a Data Source](../data/adonet/connecting-to-a-data-source.md).</span></span>  
  
2. <span data-ttu-id="d7148-111">No formulário, selecione o controle e abra exiba janela **Propriedades**.</span><span class="sxs-lookup"><span data-stu-id="d7148-111">In the form, select the control and display the **Properties** window.</span></span>  
  
3. <span data-ttu-id="d7148-112">Expanda a propriedade **(DataBindings)**.</span><span class="sxs-lookup"><span data-stu-id="d7148-112">Expand the **(DataBindings)** property.</span></span>  
  
     <span data-ttu-id="d7148-113">As propriedades geralmente mais associadas são exibidas sob a propriedade **(DataBindings)**.</span><span class="sxs-lookup"><span data-stu-id="d7148-113">The properties most often bound are displayed underneath the **(DataBindings)** property.</span></span> <span data-ttu-id="d7148-114">Por exemplo, na maioria dos controles, a propriedade **Text** é vinculada com mais frequência.</span><span class="sxs-lookup"><span data-stu-id="d7148-114">For example, in most controls, the **Text** property is most frequently bound.</span></span>  
  
4. <span data-ttu-id="d7148-115">Se a propriedade que deseja associar não for uma das propriedades comumente vinculadas, clique no botão **Elipse** (![VisualStudioEllipsesButton screenshot](./media/vbellipsesbutton.png "vbEllipsesButton")) na caixa **(Avançado)** para exibir a caixa de diálogo **Formatação e associação avançada** com uma lista completa de propriedades para esse controle.</span><span class="sxs-lookup"><span data-stu-id="d7148-115">If the property you want to bind is not one of the commonly bound properties, click the **Ellipsis** button (![VisualStudioEllipsesButton screenshot](./media/vbellipsesbutton.png "vbEllipsesButton")) in the **(Advanced)** box to display the **Formatting and Advanced Binding** dialog box with a complete list of properties for that control.</span></span>  
  
5. <span data-ttu-id="d7148-116">Selecione a propriedade que deseja associar e clique na seta suspensa em **Associação**.</span><span class="sxs-lookup"><span data-stu-id="d7148-116">Select the property you want to bind and click the drop-down arrow under **Binding**.</span></span>  
  
     <span data-ttu-id="d7148-117">Uma lista de fontes de dados disponíveis é exibida.</span><span class="sxs-lookup"><span data-stu-id="d7148-117">A list of available data sources is displayed.</span></span>  
  
6. <span data-ttu-id="d7148-118">Expanda a fonte de dados a que deseja associar até encontrar o elemento de dados individual desejado.</span><span class="sxs-lookup"><span data-stu-id="d7148-118">Expand the data source you want to bind to until you find the single data element you want.</span></span> <span data-ttu-id="d7148-119">Por exemplo, se você estiver associando a um valor de coluna na tabela do conjunto de dados, expanda o nome do conjunto de dados e o nome da tabela para exibir os nomes das colunas.</span><span class="sxs-lookup"><span data-stu-id="d7148-119">For example, if you are binding to a column value in a dataset's table, expand the name of the dataset, and then expand the table name to display column names.</span></span>  
  
7. <span data-ttu-id="d7148-120">Clique no nome de um elemento que receberá a associação.</span><span class="sxs-lookup"><span data-stu-id="d7148-120">Click the name of an element to bind to.</span></span>  
  
8. <span data-ttu-id="d7148-121">Se você estiver trabalhando na caixa de diálogo **Formatação e associação avançada**, clique em **OK** para voltar para a janela **Propriedades**.</span><span class="sxs-lookup"><span data-stu-id="d7148-121">If you were working in the **Formatting and Advanced Binding** dialog box, click **OK** to return to the **Properties** window.</span></span>  
  
9. <span data-ttu-id="d7148-122">Se deseja associar propriedades adicionais do controle, repita as etapas 3 a 7.</span><span class="sxs-lookup"><span data-stu-id="d7148-122">If you want to bind additional properties of the control, repeat steps 3 through 7.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="d7148-123">Como controles de associação simples mostram apenas um elemento de dados, é muito comum incluir a lógica de navegação em um Windows Form com controles de associação simples.</span><span class="sxs-lookup"><span data-stu-id="d7148-123">Because simple-bound controls show only a single data element, it is very typical to include navigation logic in a Windows Form with simple-bound controls.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d7148-124">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d7148-124">See also</span></span>

- <xref:System.Windows.Forms.Binding>
- [<span data-ttu-id="d7148-125">Associação de dados do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="d7148-125">Windows Forms Data Binding</span></span>](windows-forms-data-binding.md)
- [<span data-ttu-id="d7148-126">Vinculação de dados e os Windows Forms</span><span class="sxs-lookup"><span data-stu-id="d7148-126">Data Binding and Windows Forms</span></span>](data-binding-and-windows-forms.md)
