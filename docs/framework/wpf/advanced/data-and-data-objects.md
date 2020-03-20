---
title: Dados e objetos de dados
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data transfer [WPF], drag-and-drop
- DataFormats class [WPF]
- DataObject class [WPF]
ms.assetid: 5967d557-1867-420f-a524-ae3af78402da
ms.openlocfilehash: 532c254f997da183b073ddc9e00b4364ecfcd739
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186347"
---
# <a name="data-and-data-objects"></a>Dados e objetos de dados
Dados que são transferidos como parte de uma operação do tipo "arrastar e soltar" são armazenados em um objeto de dados.  Conceitualmente, um objeto de dados consiste em um ou mais dos seguintes pares:  
  
- Um <xref:System.Object> que contém os dados reais.  
  
- Um identificador de formato de dados correspondente.  
  
 Os dados em si podem consistir <xref:System.Object>em qualquer coisa que possa ser representada como base.  O formato de dados <xref:System.Type> correspondente é uma seqüência ou que fornece uma dica sobre em que formato os dados estão.  Objetos de dados dão suporte à hospedagem de vários pares de formato de dados/dados. Isso permite que um único objeto de dados forneça dados em vários formatos.  
  
<a name="Data_and_Data_Objects"></a>
## <a name="data-objects"></a>Objetos de dados  
 Todos os objetos <xref:System.Windows.IDataObject> de dados devem implementar a interface, que fornece o seguinte conjunto padrão de métodos que permitem e facilitam a transferência de dados.  
  
|Método|Resumo|  
|------------|-------------|  
|<xref:System.Windows.IDataObject.GetData%2A>|Recupera um objeto de dados em um formato de dados especificado.|  
|<xref:System.Windows.IDataObject.GetDataPresent%2A>|Verifica se os dados estão disponíveis em um formato especificado ou se podem ser convertidos para esse formato.|  
|<xref:System.Windows.IDataObject.GetFormats%2A>|Retorna uma lista de formatos em que os dados deste objeto de dados estão armazenados ou em que podem ser convertidos.|  
|<xref:System.Windows.IDataObject.SetData%2A>|Armazena os dados especificados neste objeto de dados.|  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]fornece uma implementação <xref:System.Windows.DataObject> básica da <xref:System.Windows.IDataObject> classe. A <xref:System.Windows.DataObject> classe de ações é suficiente para muitos cenários comuns de transferência de dados.  
  
 Há diversos formatos predefinidos, como bitmap, CSV, arquivo, HTML, RTF, cadeia de caracteres, texto e áudio. Para obter informações sobre formatos de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]dados <xref:System.Windows.DataFormats> pré-definidos fornecidos, consulte o tópico de referência da classe.  
  
 Normalmente, objetos de dados incluem um recurso para converter automaticamente dados armazenados em um formato para um formato diferente ao extrair os dados; esse recurso é conhecido como conversão automática. Ao consultar os formatos de dados disponíveis em um objeto de dados, os formatos de <xref:System.Windows.DataObject.GetFormats%28System.Boolean%29> dados <xref:System.Windows.DataObject.GetDataPresent%28System.String%2CSystem.Boolean%29> conversíveis automáticos podem ser filtrados a partir de formatos de dados nativos, chamando o método ou especificando o `autoConvert` parâmetro como `false`.  Ao adicionar dados a um <xref:System.Windows.DataObject.SetData%28System.String%2CSystem.Object%2CSystem.Boolean%29> objeto de dados com o método, `autoConvert` a `false`conversão automática de dados pode ser proibida definindo o parâmetro para .  
  
<a name="Working_with_Data_Objects"></a>
## <a name="working-with-data-objects"></a>Trabalhando com objetos de dados  
 Esta seção descreve técnicas comuns para criar e trabalhar com objetos de dados.  
  
### <a name="creating-new-data-objects"></a>Criando novos objetos de dados  
 A <xref:System.Windows.DataObject> classe fornece vários construtores sobrecarregados que <xref:System.Windows.DataObject> facilitam a povoação de uma nova instância com um único par de formatos de dados/dados.  
  
 O código de exemplo a seguir cria um novo objeto <xref:System.Windows.DataObject.%23ctor%2A><xref:System.Windows.DataObject.%23ctor(System.String,System.Object)>de dados e usa um dos construtores sobrecarregados ( ) para inicializar o objeto de dados com uma seqüência e um formato de dados especificado.  Neste caso, o formato de dados é especificado por uma seqüência; a <xref:System.Windows.DataFormats> classe fornece um conjunto de strings de tipo pré-definidas. A conversão automática dos dados armazenados é permitida por padrão.  
  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_CreateDataObject_TypeString](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_createdataobject_typestring)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_CreateDataObject_TypeString](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_createdataobject_typestring)]  
  
 Para obter mais exemplos de código que cria um objeto de dados, consulte [Criar um objeto de dados](how-to-create-a-data-object.md).  
  
### <a name="storing-data-in-multiple-formats"></a>Armazenando dados em vários formatos  
 Um único objeto de dados é capaz de armazenar dados em vários formatos.   O uso estratégico de vários formatos de dados em um único objeto de dados potencialmente torna o objeto de dados consumível por uma maior variedade de destinos alvo do que se apenas um único formato de dados pudesse ser representado.  Observe que, de modo geral, uma fonte deve ser agnóstica quanto aos formatos de dados que são consumíveis por possíveis alvos.  
  
 O exemplo a seguir <xref:System.Windows.DataObject.SetData%28System.String%2CSystem.Object%29> mostra como usar o método para adicionar dados a um objeto de dados em vários formatos.  
  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_StoreMultipleFormats](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_storemultipleformats)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_StoreMultipleFormats](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_storemultipleformats)]  
  
### <a name="querying-a-data-object-for-available-formats"></a>Consultando um objeto de dados para os formatos disponíveis  
 Como um único objeto de dados pode conter um número arbitrário de formatos de dados, os objetos de dados incluem recursos para recuperar uma lista dos formatos de dados disponíveis.  
  
 O código de <xref:System.Windows.DataObject.GetFormats%2A> exemplo a seguir usa a sobrecarga para obter uma matriz de strings denotando todos os formatos de dados disponíveis em um objeto de dados (nativo e por conversão automática).  
  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_GetAllDataFormats](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_getalldataformats)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_GetAllDataFormats](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_getalldataformats)]  
  
 Para obter mais exemplos de códigos que consultam um objeto de dados quanto aos formatos de dados disponíveis, consulte [Listar os formatos de dados em um objeto de dados](how-to-list-the-data-formats-in-a-data-object.md).  Para obter exemplos de consulta a um objeto de dados quanto à presença de um formato de dados específico, consulte [Determinar se um formato de dados está presente em um objeto de dados](how-to-determine-if-a-data-format-is-present-in-a-data-object.md).  
  
### <a name="retrieving-data-from-a-data-object"></a>Recuperando dados de um objeto de dados  
 Recuperar dados de um objeto de dados em um <xref:System.Windows.DataObject.GetData%2A> formato específico simplesmente envolve chamar um dos métodos e especificar o formato de dados desejado.  Um dos <xref:System.Windows.DataObject.GetDataPresent%2A> métodos pode ser usado para verificar a presença de um determinado formato de dados.  <xref:System.Windows.DataObject.GetData%2A>retorna os dados <xref:System.Object>em um; dependendo do formato de dados, este objeto pode ser lançado para um recipiente específico do tipo.  
  
 O código de <xref:System.Windows.DataObject.GetDataPresent%28System.String%29> exemplo a seguir usa a sobrecarga para verificar se um formato de dados especificado está disponível (nativo ou por conversão automática). Se o formato especificado estiver disponível, o <xref:System.Windows.DataObject.GetData%28System.String%29> exemplo recuperará os dados usando o método.  
  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_GetSpecificDataFormat](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_getspecificdataformat)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_GetSpecificDataFormat](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_getspecificdataformat)]  
  
 Para obter mais exemplos de códigos que recuperam dados de um objeto de dados, consulte [Recuperar dados em um formato de dados específico](how-to-retrieve-data-in-a-particular-data-format.md).  
  
### <a name="removing-data-from-a-data-object"></a>Removendo dados de um objeto de dados  
 Os dados não podem ser removidos diretamente de um objeto de dados.  Para remover efetivamente os dados de um objeto de dados, siga estas etapas:  
  
1. Crie um novo objeto de dados que conterá somente os dados que você deseja manter.  
  
2. "Copie" os dados desejados do objeto de dados antigo para o novo objeto de dados.  Para copiar os dados, <xref:System.Windows.DataObject.GetData%2A> use um dos <xref:System.Object> métodos para recuperar um que <xref:System.Windows.DataObject.SetData%2A> contenha os dados brutos e, em seguida, use um dos métodos para adicionar os dados ao novo objeto de dados.  
  
3. Substitua o objeto de dados antigo pelo novo.  
  
> [!NOTE]
> Os <xref:System.Windows.DataObject.SetData%2A> métodos só adicionam dados a um objeto de dados; eles não substituem dados, mesmo que o formato de dados e dados sejam exatamente os mesmos de uma chamada anterior. Chamar <xref:System.Windows.DataObject.SetData%2A> duas vezes o mesmo formato de dados e dados resultará na presença do formato dados/dados duas vezes no objeto de dados.
