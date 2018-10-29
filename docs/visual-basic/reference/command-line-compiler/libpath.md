---
title: -libpath
ms.date: 03/10/2018
helpviewer_keywords:
- libpath compiler option [Visual Basic]
- /libpath compiler option [Visual Basic]
- -libpath compiler option [Visual Basic]
ms.assetid: 5f1c26c9-3455-4e89-bdf3-b12d6c2e655b
ms.openlocfilehash: d713a63c9503581f38048fe79c559883dc96efd2
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/29/2018
ms.locfileid: "50202966"
---
# <a name="-libpath"></a>-libpath
Especifica o local dos assemblies referenciados.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
-libpath:dirList  
```  
  
## <a name="arguments"></a>Arguments  
  
|Termo|Definição|  
|---|---|  
|`dirList`|Necessário. Lista delimitada por ponto e vírgula de diretórios para o compilador examinar se um assembly referenciado não for encontrada no diretório de trabalho atual (o diretório do qual você está invocando o compilador) ou o diretório do sistema do common language runtime. Se o nome do diretório contém um espaço, coloque o nome entre aspas ("").|  
  
## <a name="remarks"></a>Comentários  
 O `-libpath` opção especifica o local dos assemblies referenciados pelo [-referência](../../../visual-basic/reference/command-line-compiler/reference.md) opção.  
  
 O compilador pesquisa referências de assembly que não são totalmente qualificadas na seguinte ordem:  
  
1.  Diretório de trabalho atual. Esse é o diretório do qual o compilador é invocado.  
  
2.  O diretório de sistema do Common Language Runtime.  
  
3.  Diretórios especificados pela `/libpath`.  
  
4.  Diretórios especificados pela variável de ambiente LIB.  
  
 O `-libpath` opção é aditivo; especificá-lo mais de uma vez acrescenta a valores anteriores.  
  
 Use `-reference` para especificar uma referência de assembly.  
  
|Configurar /libpath no Visual Studio ambiente de desenvolvimento integrado|  
|---|  
|1.  Selecione um projeto no **Gerenciador de Soluções**. No menu **Projeto**, clique em **Propriedades**. <br />2.  Clique na guia **Referências**.<br />3.  Clique o **caminhos de referência...**  botão.<br />4.  No **caminhos de referência** caixa de diálogo, digite o nome do diretório na **pasta:** caixa.<br />5.  Clique em **adicionar pasta**.|  
  
## <a name="example"></a>Exemplo  
 O seguinte código compila `T2.vb` para criar um arquivo .exe. O compilador procura no diretório de trabalho, no diretório raiz da unidade c e no diretório da unidade c: novos Assemblies referências de assembly.  
  
```console  
vbc -libpath:c:\;"c:\New Assemblies" -reference:t2.dll t2.vb  
```  
  
## <a name="see-also"></a>Consulte também  
 [Assemblies e o Cache de Assembly Global](../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md)  
 [Compilador de linha de comando do Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)  
 [Linhas de Comando de Compilação de Exemplo](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
