---
title: Objeto My. Resources (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- My.Resources
- My.Resources.MyResources.ResourceManager
- My.Resources.MyResources.Culture
helpviewer_keywords:
- My.Resources object
ms.assetid: 34c3f2dc-7b87-432c-9d5f-17ea666bb266
ms.openlocfilehash: 41b6eaa39abfab6cda943162c5c10d1cbeaa9e49
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/08/2018
ms.locfileid: "44186559"
---
# <a name="myresources-object"></a>Objeto My.Resources
Fornece classes e propriedades para acessar os recursos do aplicativo.  
  
## <a name="remarks"></a>Comentários  
 O `My.Resources` objeto fornece acesso aos recursos do aplicativo e permite que você dinamicamente recuperar recursos para seu aplicativo. Para obter mais informações, consulte [Gerenciando recursos de aplicativo (.NET)](/visualstudio/ide/managing-application-resources-dotnet).  
  
 O `My.Resources` objeto expõe apenas recursos globais. Ele não fornece acesso aos arquivos de recurso associados a formulários. Você deve acessar os recursos de formulário do formulário.  
  
 Você pode acessar arquivos de recurso específico de cultura do aplicativo do `My.Resources` objeto. Por padrão, o `My.Resources` objeto pesquisa os recursos do arquivo de recurso que corresponda à cultura no <xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase.UICulture%2A> propriedade. No entanto, você pode substituir esse comportamento e especificar uma determinada cultura a ser usado para os recursos. Para saber mais, veja [Recursos em aplicativos da área de trabalho](../../../framework/resources/index.md).  
  
## <a name="properties"></a>Propriedades  
 As propriedades do `My.Resources` objeto fornecer acesso somente leitura aos recursos de seu aplicativo. Para adicionar ou remover recursos, use o **Designer de projeto**. Você pode acessar os recursos adicionados por meio de **Designer de projeto** usando `My.Resources.``resourceName`.  
  
 Você também pode adicionar ou remover arquivos de recurso selecionando o seu projeto no **Gerenciador de soluções** e clicando em **Adicionar Novo Item** ou **Adicionar Item existente** do  **Projeto** menu. Você pode acessar recursos adicionados dessa maneira, usando `My.Resources.``resourceFileName`.`resourceName`.  
  
 Cada recurso tem um nome, categoria e valor, e essas configurações de recurso determinam como a propriedade para acessar o recurso aparece no `My.Resources` objeto. Para recursos adicionados na **Designer de projeto**:  
  
-   O nome determina o nome da propriedade,  
  
-   Os dados de recursos são o valor da propriedade,  
  
-   A categoria determina o tipo da propriedade:  
  
|Categoria|Tipo de dados de propriedade|  
|---|---|  
|**Cadeias de Caracteres**|[Cadeia de caracteres](../../../visual-basic/language-reference/data-types/string-data-type.md)|  
|**Imagens**|<xref:System.Drawing.Bitmap>|  
|**Ícones**|<xref:System.Drawing.Icon>|  
|**Áudio**|<xref:System.IO.UnmanagedMemoryStream><br /><br /> O <xref:System.IO.UnmanagedMemoryStream> classe deriva de <xref:System.IO.Stream> classe, para que possa ser usado com métodos que usam fluxos, como o <xref:Microsoft.VisualBasic.Devices.Audio.Play%2A> método.|  
|**Arquivos**|-   [Cadeia de caracteres](../../../visual-basic/language-reference/data-types/string-data-type.md) para arquivos de texto.<br />-   <xref:System.Drawing.Bitmap> para arquivos de imagem.<br />-   <xref:System.Drawing.Icon> para arquivos de ícone.<br />-   <xref:System.IO.UnmanagedMemoryStream> para arquivos de som.|  
|**Outros**|Determinadas pelas informações no designer de **tipo** coluna.|  
  
## <a name="classes"></a>Classes  
 O `My.Resources` objeto expõe cada arquivo de recurso como uma classe com propriedades compartilhadas. O nome da classe é o mesmo que o nome do arquivo de recurso. Conforme descrito na seção anterior, os recursos em um arquivo de recurso são expostos como propriedades na classe.  
  
## <a name="example"></a>Exemplo  
 Este exemplo define o título de um formulário para o recurso de cadeia de caracteres chamado `Form1Title` no arquivo de recurso do aplicativo. Para o exemplo funcione, o aplicativo deve ter uma cadeia de caracteres denominada `Form1Title` em seu arquivo de recurso.  
  
 [!code-vb[VbVbalrMyResources#1](../../../visual-basic/developing-apps/programming/app-settings/codesnippet/VisualBasic/my-resources-object_1.vb)]  
  
## <a name="example"></a>Exemplo  
 Este exemplo define o ícone do formulário para o ícone chamado `Form1Icon` que é armazenado no arquivo de recurso do aplicativo. Para o exemplo funcione, o aplicativo deve ter um ícone chamado `Form1Icon` em seu arquivo de recurso.  
  
 [!code-vb[VbVbalrMyResources#2](../../../visual-basic/developing-apps/programming/app-settings/codesnippet/VisualBasic/my-resources-object_2.vb)]  
  
## <a name="example"></a>Exemplo  
 Este exemplo define a imagem de plano de fundo de um formulário para o recurso de imagem chamado `Form1Background`, que está no arquivo de recurso do aplicativo. Para esse exemplo funcione, o aplicativo deve ter um recurso de imagem chamado `Form1Background` em seu arquivo de recurso.  
  
 [!code-vb[VbVbalrMyResources#3](../../../visual-basic/developing-apps/programming/app-settings/codesnippet/VisualBasic/my-resources-object_3.vb)]  
  
## <a name="example"></a>Exemplo  
 Este exemplo reproduz o som que é armazenado como um recurso de áudio chamado `Form1Greeting` no arquivo de recurso do aplicativo. Para o exemplo funcione, o aplicativo deve ter um recurso de áudio chamado `Form1Greeting` em seu arquivo de recurso. O `My.Computer.Audio.Play` método está disponível somente para aplicativos Windows Forms.  
  
 [!code-vb[VbVbalrMyResources#4](../../../visual-basic/developing-apps/programming/app-settings/codesnippet/VisualBasic/my-resources-object_4.vb)]  
  
## <a name="example"></a>Exemplo  
 Este exemplo recupera a versão de cultura francesa de um recurso de cadeia de caracteres do aplicativo. O recurso é chamado `Message`. Para alterar a cultura que o `My.Resources` usa o objeto, o exemplo usa <xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase.ChangeUICulture%2A>.  
  
 Para esse exemplo funcione, o aplicativo deve ter uma cadeia de caracteres denominada `Message` em seu recurso de arquivo e o aplicativo devem ter a versão de cultura francesa desse arquivo de recursos, Resources.fr-FR. resx. Se o aplicativo não tiver a versão de cultura francesa do arquivo de recurso, o `My.Resource` objeto recupera o recurso do arquivo de recurso de cultura padrão.  
  
 [!code-vb[VbVbalrMyResources#10](../../../visual-basic/developing-apps/programming/app-settings/codesnippet/VisualBasic/my-resources-object_5.vb)]  
  
## <a name="see-also"></a>Consulte também  
 [Gerenciando recursos de aplicativo (.NET)](/visualstudio/ide/managing-application-resources-dotnet)  
 [Recursos em aplicativos de área de trabalho](../../../framework/resources/index.md)  

