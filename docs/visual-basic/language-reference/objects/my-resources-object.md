---
title: Objeto My.Resources
ms.date: 07/20/2015
f1_keywords:
- My.Resources
- My.Resources.MyResources.ResourceManager
- My.Resources.MyResources.Culture
helpviewer_keywords:
- My.Resources object
ms.assetid: 34c3f2dc-7b87-432c-9d5f-17ea666bb266
ms.openlocfilehash: 7f5d81194123ad2151a494a3cb79aa1955e0fdad
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74350336"
---
# <a name="myresources-object"></a>Objeto My.Resources
Fornece propriedades e classes para acessar os recursos do aplicativo.  
  
## <a name="remarks"></a>Comentários  
 O objeto `My.Resources` fornece acesso aos recursos do aplicativo e permite que você recupere dinamicamente os recursos para seu aplicativo. Para obter mais informações, consulte [Gerenciando recursos de aplicativos (.net)](/visualstudio/ide/managing-application-resources-dotnet).  
  
 O objeto `My.Resources` expõe apenas recursos globais. Ele não fornece acesso aos arquivos de recursos associados aos formulários. Você deve acessar os recursos do formulário no formulário.  
  
 Você pode acessar os arquivos de recursos específicos da cultura do aplicativo por meio do objeto `My.Resources`. Por padrão, o objeto `My.Resources` pesquisa os recursos do arquivo de recurso que corresponde à cultura na propriedade <xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase.UICulture%2A>. No entanto, você pode substituir esse comportamento e especificar uma cultura específica a ser usada para os recursos. Para saber mais, veja [Recursos em aplicativos da área de trabalho](../../../framework/resources/index.md).  
  
## <a name="properties"></a>Propriedades  
 As propriedades do objeto `My.Resources` fornecem acesso somente leitura aos recursos do aplicativo. Para adicionar ou remover recursos, use o **Designer de projeto**. Você pode acessar os recursos adicionados por meio do **Designer de projeto** usando `My.Resources.`*resourceName*.  
  
 Você também pode adicionar ou remover arquivos de recursos selecionando seu projeto no **Gerenciador de soluções** e clicando em **Adicionar novo item** ou **Adicionar item existente** no menu **projeto** . Você pode acessar os recursos adicionados dessa maneira usando `My.Resources.`*resourceFileName*`.`*resourceName*.  
  
 Cada recurso tem um nome, categoria e valor, e essas configurações de recurso determinam como a propriedade para acessar o recurso aparece no objeto `My.Resources`. Para recursos adicionados no **Designer de projeto**:  
  
- O nome determina o nome da propriedade,  
  
- Os dados de recurso são o valor da propriedade,  
  
- A categoria determina o tipo da propriedade:  
  
|Categoria|Tipo de dados de propriedade|  
|---|---|  
|**Cadeias de Caracteres**|[Cadeia de caracteres](../../../visual-basic/language-reference/data-types/string-data-type.md)|  
|**Imagens**|<xref:System.Drawing.Bitmap>|  
|**Ícones**|<xref:System.Drawing.Icon>|  
|**Áudio**|<xref:System.IO.UnmanagedMemoryStream><br /><br /> A classe <xref:System.IO.UnmanagedMemoryStream> deriva da classe <xref:System.IO.Stream>, portanto, ela pode ser usada com métodos que usam fluxos, como o método <xref:Microsoft.VisualBasic.Devices.Audio.Play%2A>.|  
|**Arquivos**|-   [cadeia de caracteres](../../../visual-basic/language-reference/data-types/string-data-type.md) para arquivos de texto.<br />-   <xref:System.Drawing.Bitmap> para arquivos de imagem.<br />-   <xref:System.Drawing.Icon> para arquivos de ícone.<br />-   <xref:System.IO.UnmanagedMemoryStream> para arquivos de som.|  
|**Outros**|Determinado pelas informações na coluna **Type** do designer.|  
  
## <a name="classes"></a>Classes  
 O objeto `My.Resources` expõe cada arquivo de recurso como uma classe com propriedades compartilhadas. O nome da classe é o mesmo que o nome do arquivo de recurso. Conforme descrito na seção anterior, os recursos em um arquivo de recurso são expostos como propriedades na classe.  
  
## <a name="example"></a>Exemplo  
 Este exemplo define o título de um formulário para o recurso de cadeia de caracteres chamado `Form1Title` no arquivo de recurso do aplicativo. Para que o exemplo funcione, o aplicativo deve ter uma cadeia de caracteres chamada `Form1Title` em seu arquivo de recurso.  
  
 [!code-vb[VbVbalrMyResources#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyResources/VB/Form1.vb#1)]  
  
## <a name="example"></a>Exemplo  
 Este exemplo define o ícone do formulário para o ícone chamado `Form1Icon` que é armazenado no arquivo de recurso do aplicativo. Para que o exemplo funcione, o aplicativo deve ter um ícone chamado `Form1Icon` em seu arquivo de recurso.  
  
 [!code-vb[VbVbalrMyResources#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyResources/VB/Form1.vb#2)]  
  
## <a name="example"></a>Exemplo  
 Este exemplo define a imagem de plano de fundo de um formulário para o recurso de imagem chamado `Form1Background`, que está no arquivo de recurso do aplicativo. Para que este exemplo funcione, o aplicativo deve ter um recurso de imagem chamado `Form1Background` em seu arquivo de recurso.  
  
 [!code-vb[VbVbalrMyResources#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyResources/VB/Form1.vb#3)]  
  
## <a name="example"></a>Exemplo  
 Este exemplo reproduz o som que é armazenado como um recurso de áudio chamado `Form1Greeting` no arquivo de recursos do aplicativo. Para que o exemplo funcione, o aplicativo deve ter um recurso de áudio chamado `Form1Greeting` em seu arquivo de recurso. O método `My.Computer.Audio.Play` está disponível somente para aplicativos Windows Forms.  
  
 [!code-vb[VbVbalrMyResources#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyResources/VB/Form1.vb#4)]  
  
## <a name="example"></a>Exemplo  
 Este exemplo recupera a versão de cultura francesa de um recurso de cadeia de caracteres do aplicativo. O recurso é nomeado `Message`. Para alterar a cultura que o objeto de `My.Resources` usa, o exemplo usa <xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase.ChangeUICulture%2A>.  
  
 Para que este exemplo funcione, o aplicativo deve ter uma cadeia de caracteres chamada `Message` em seu arquivo de recurso e o aplicativo deve ter a versão de cultura francesa desse arquivo de recurso, Resources.fr-FR. resx. Se o aplicativo não tiver a versão de cultura francesa do arquivo de recurso, o objeto `My.Resource` recuperará o recurso do arquivo de recurso de cultura padrão.  
  
 [!code-vb[VbVbalrMyResources#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyResources/VB/Form1.vb#10)]  
  
## <a name="see-also"></a>Consulte também

- [Gerenciando recursos de aplicativo (.NET)](/visualstudio/ide/managing-application-resources-dotnet)
- [Recursos em aplicativos de área de trabalho](../../../framework/resources/index.md)
