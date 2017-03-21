---
title: /libpath | Documentos do Microsoft
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- libpath compiler option [Visual Basic]
- /libpath compiler option [Visual Basic]
- -libpath compiler option [Visual Basic]
ms.assetid: 5f1c26c9-3455-4e89-bdf3-b12d6c2e655b
caps.latest.revision: 16
author: stevehoag
ms.author: shoag
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
ms.openlocfilehash: cc534e782cff34f0c4882f3da2af973fed69ff80
ms.lasthandoff: 03/13/2017

---
# <a name="libpath"></a>/libpath
Especifica o local dos assemblies referenciados.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
/libpath:dirList  
```  
  
## <a name="arguments"></a>Arguments  
  
|Termo|Definição|  
|---|---|  
|`dirList`|Necessário. Lista delimitada por ponto e vírgula de diretórios para o compilador ver se um assembly referenciado não foi encontrada no diretório de trabalho atual (o diretório do qual você está chamando o compilador) ou o diretório do sistema do common language runtime. Se o nome do diretório contém um espaço, coloque o nome entre aspas ("").|  
  
## <a name="remarks"></a>Comentários  
 O `/libpath` opção especifica o local dos assemblies referenciados pelo [/Reference](../../../visual-basic/reference/command-line-compiler/reference.md) opção.  
  
 O compilador procura por referências de assembly que não são totalmente qualificadas na seguinte ordem:  
  
1.  Diretório de trabalho atual. Este é o diretório do qual o compilador é chamado.  
  
2.  Diretório do common language runtime system.  
  
3.  Diretórios especificados pela `/libpath`.  
  
4.  Diretórios especificados pela variável de ambiente LIB.  
  
 O `/libpath` opção é aditiva; especificando mais de uma vez acrescenta a valores anteriores.  
  
 Use `/reference` para especificar uma referência de assembly.  
  
|Configurar /libpath no Visual Studio ambiente de desenvolvimento integrado|  
|---|  
|1.  Tenha um projeto selecionado no **Solution Explorer**. No menu **Projeto**, clique em **Propriedades**. Para obter mais informações, consulte [Introdução ao Designer de Projeto](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7).<br />2.  Clique o **referências** guia.<br />3.  Clique a **caminhos de referência... ** botão.<br />4.  No **caminhos de referência** caixa de diálogo, digite o nome do diretório no **pasta:** caixa.<br />5.  Clique em **adicionar pasta**.|  
  
## <a name="example"></a>Exemplo  
 O seguinte código compila `T2.vb` para criar um arquivo .exe. O compilador procura no diretório de trabalho, no diretório raiz da unidade c e no diretório da unidade c novos Assemblies de referências de assembly.  
  
```  
vbc /libpath:c:\;"c:\New Assemblies" /reference:t2.dll t2.vb  
```  
  
## <a name="see-also"></a>Consulte também  
 [Assemblies e o Cache de Assembly Global](../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md)   
 [Compilador de linha de comando do Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)   
 [Linhas de Comando de Compilação de Exemplo](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
