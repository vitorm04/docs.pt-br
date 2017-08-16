---
title: Objeto My. Resources | Documentos do Microsoft
ms.date: 2015-07-20
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- My.Resources
- My.Resources.MyResources.ResourceManager
- My.Resources.MyResources.Culture
dev_langs:
- VB
helpviewer_keywords:
- My.Resources object
ms.assetid: 34c3f2dc-7b87-432c-9d5f-17ea666bb266
caps.latest.revision: 22
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 6ad5bd4e33438256719b59cb0936cf6bc8525ab1
ms.lasthandoff: 03/13/2017

---
# <a name="myresources-object"></a>Objeto My.Resources
Fornece classes e propriedades para acessar os recursos do aplicativo.  
  
## <a name="remarks"></a>Comentários  
 O `My.Resources` objeto fornece acesso aos recursos do aplicativo e permite que você dinamicamente recuperar recursos para seu aplicativo. Para obter mais informações, consulte [recursos de gerenciamento de aplicativo (.NET)](https://docs.microsoft.com/visualstudio/ide/managing-application-resources-dotnet).  
  
 O `My.Resources` objeto expõe apenas recursos globais. Ele não fornece acesso aos arquivos de recursos associados a formulários. Você deve acessar os recursos de formulário do formulário. Para obter mais informações, consulte [Passo a passo: Localizando o Windows Forms](http://msdn.microsoft.com/en-us/9a96220d-a19b-4de0-9f48-01e5d82679e5).  
  
 Você pode acessar arquivos de recurso com cultura específica do aplicativo do `My.Resources` objeto. Por padrão, o `My.Resources` objeto procura recursos do arquivo de recurso que corresponda a cultura do <xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase.UICulture%2A>propriedade.</xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase.UICulture%2A> No entanto, você pode substituir esse comportamento e especificar uma cultura específica a ser usado para os recursos. Para obter mais informações, consulte [recursos em aplicativos de área de trabalho](http://msdn.microsoft.com/library/8ad495d4-2941-40cf-bf64-e82e85825890).  
  
## <a name="properties"></a>Propriedades  
 As propriedades do `My.Resources` objeto fornece acesso somente leitura aos recursos de seu aplicativo. Para adicionar ou remover recursos, use o **Project Designer**. Para obter mais informações, consulte [como: Adicionar ou remover recursos](http://msdn.microsoft.com/en-us/7b77bc06-3952-4799-b029-def3f8f7f88d). Você pode acessar recursos adicionados por meio de **Project Designer** usando `My.Resources.``resourceName`.  
  
 Você também pode adicionar ou remover arquivos de recursos selecionando o seu projeto no **Solution Explorer** e clicando em **Adicionar Novo Item** ou **Add Existing Item** do **projeto** menu. Você pode acessar recursos adicionados dessa maneira usando `My.Resources.``resourceFileName`.`resourceName`.  
  
 Cada recurso tem um nome, categoria e valor, e essas configurações de recurso determinam como a propriedade para acessar o recurso aparece no `My.Resources` objeto. Para recursos adicionados no **Project Designer**:  
  
-   O nome determina o nome da propriedade,  
  
-   Os dados de recursos são o valor da propriedade,  
  
-   A categoria determina o tipo da propriedade:  
  
|Categoria|Tipo de dados de propriedade|  
|---|---|  
|**Cadeias de Caracteres**|[Cadeia de caracteres](../../../visual-basic/language-reference/data-types/string-data-type.md)|  
|**Imagens**|<xref:System.Drawing.Bitmap></xref:System.Drawing.Bitmap>|  
|**Ícones**|<xref:System.Drawing.Icon></xref:System.Drawing.Icon>|  
|**Áudio**|<xref:System.IO.UnmanagedMemoryStream></xref:System.IO.UnmanagedMemoryStream><br /><br /> O <xref:System.IO.UnmanagedMemoryStream>classe deriva de <xref:System.IO.Stream>classe, portanto ele pode ser usado com métodos que usam fluxos, como o <xref:Microsoft.VisualBasic.Devices.Audio.Play%2A>método.</xref:Microsoft.VisualBasic.Devices.Audio.Play%2A> </xref:System.IO.Stream> </xref:System.IO.UnmanagedMemoryStream>|  
|**Arquivos**|-   [Cadeia de caracteres](../../../visual-basic/language-reference/data-types/string-data-type.md) para arquivos de texto.<br />- <xref:System.Drawing.Bitmap>para arquivos de imagem.</xref:System.Drawing.Bitmap><br />- <xref:System.Drawing.Icon>para arquivos de ícone.</xref:System.Drawing.Icon><br />- <xref:System.IO.UnmanagedMemoryStream>para arquivos de som.</xref:System.IO.UnmanagedMemoryStream>|  
|**Outros**|Determinadas pelas informações no designer de **tipo** coluna.|  
  
## <a name="classes"></a>Classes  
 O `My.Resources` objeto expõe cada arquivo de recurso como uma classe com propriedades compartilhadas. O nome da classe é o mesmo que o nome do arquivo de recurso. Conforme descrito na seção anterior, os recursos em um arquivo de recurso são expostos como propriedades na classe.  
  
## <a name="example"></a>Exemplo  
 Este exemplo define o título de um formulário para o recurso de cadeia de caracteres chamado `Form1Title` no arquivo de recurso do aplicativo. Por exemplo funcionar, o aplicativo deve ter uma cadeia de caracteres chamada `Form1Title` em seu arquivo de recurso. Para obter mais informações, consulte [como: Adicionar ou remover recursos](http://msdn.microsoft.com/en-us/7b77bc06-3952-4799-b029-def3f8f7f88d).  
  
 [!code-vb[VbVbalrMyResources n º&1;](../../../visual-basic/developing-apps/programming/app-settings/codesnippet/VisualBasic/my-resources-object_1.vb)]  
  
## <a name="example"></a>Exemplo  
 Este exemplo define o ícone do formulário para o ícone chamado `Form1Icon` que é armazenado no arquivo de recurso do aplicativo. Por exemplo funcionar, o aplicativo deve ter um ícone chamado `Form1Icon` em seu arquivo de recurso.  
  
 [!code-vb[VbVbalrMyResources n º&2;](../../../visual-basic/developing-apps/programming/app-settings/codesnippet/VisualBasic/my-resources-object_2.vb)]  
  
## <a name="example"></a>Exemplo  
 Este exemplo define a imagem de plano de fundo de um formulário para o recurso de imagem chamado `Form1Background`, que está no arquivo de recurso do aplicativo. Para esse exemplo funcione, o aplicativo deve ter um recurso de imagem nomeado `Form1Background` em seu arquivo de recurso.  
  
 [!code-vb[VbVbalrMyResources n º&3;](../../../visual-basic/developing-apps/programming/app-settings/codesnippet/VisualBasic/my-resources-object_3.vb)]  
  
## <a name="example"></a>Exemplo  
 Este exemplo reproduz o som é armazenado como um recurso de áudio chamado `Form1Greeting` no arquivo de recurso do aplicativo. Por exemplo funcionar, o aplicativo deve ter um recurso de áudio chamado `Form1Greeting` em seu arquivo de recurso. O `My.Computer.Audio.Play` método está disponível somente para aplicativos Windows Forms.  
  
 [!code-vb[VbVbalrMyResources n º&4;](../../../visual-basic/developing-apps/programming/app-settings/codesnippet/VisualBasic/my-resources-object_4.vb)]  
  
## <a name="example"></a>Exemplo  
 Este exemplo recupera a versão de cultura francesa de um recurso de cadeia de caracteres do aplicativo. O recurso chamado `Message`. Para alterar a cultura que o `My.Resources` usa o objeto, o exemplo usa <xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase.ChangeUICulture%2A>.</xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase.ChangeUICulture%2A>  
  
 Para esse exemplo funcione, o aplicativo deve ter uma cadeia de caracteres chamada `Message` em seu recurso de arquivo e o aplicativo devem ter a versão de cultura francesa desse arquivo de recursos, Resources.fr-FR. Para obter mais informações, consulte [como: Adicionar ou remover recursos](http://msdn.microsoft.com/en-us/7b77bc06-3952-4799-b029-def3f8f7f88d). Se o aplicativo não tiver a versão de cultura francesa do arquivo de recurso, o `My.Resource` objeto recupera o recurso do arquivo de recurso de cultura padrão.  
  
 [!code-vb[VbVbalrMyResources n º&10;](../../../visual-basic/developing-apps/programming/app-settings/codesnippet/VisualBasic/my-resources-object_5.vb)]  
  
## <a name="see-also"></a>Consulte também  
 [Como: Adicionar ou remover recursos](http://msdn.microsoft.com/en-us/7b77bc06-3952-4799-b029-def3f8f7f88d)   
 [Gerenciando recursos de aplicativo (.NET)](https://docs.microsoft.com/visualstudio/ide/managing-application-resources-dotnet)   
 [Recursos em aplicativos de área de trabalho](http://msdn.microsoft.com/library/8ad495d4-2941-40cf-bf64-e82e85825890)   
 [Passo a passo: Localizando Windows Forms](http://msdn.microsoft.com/en-us/9a96220d-a19b-4de0-9f48-01e5d82679e5)
