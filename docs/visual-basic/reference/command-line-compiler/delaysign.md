---
title: -delaysign
ms.date: 03/10/2018
helpviewer_keywords:
- delaysign compiler option [Visual Basic]
- -delaysign compiler option [Visual Basic]
- -delaysign compiler option [Visual Basic]
ms.assetid: c76e61a4-1884-4252-9fb2-377f99caa690
ms.openlocfilehash: 770dcad385c522a548a0c6fd3b6ef02dfbac82f5
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59334595"
---
# <a name="-delaysign"></a>-delaysign
Especifica se o assembly será assinado total ou parcialmente.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
-delaysign[+ | -]  
```  
  
## <a name="arguments"></a>Arguments  
 `+` &#124; `-`  
 Opcional. Use `-delaysign-` se você quiser um assembly totalmente assinado. Use `-delaysign+` se você deseja colocar a chave pública no assembly e reserva espaço para o hash com sinal. O padrão é `-delaysign-`.  
  
## <a name="remarks"></a>Comentários  
 O `-delaysign` opção não tem nenhum efeito a menos que usado com [- keyfile](../../../visual-basic/reference/command-line-compiler/keyfile.md) ou [- keycontainer](../../../visual-basic/reference/command-line-compiler/keycontainer.md).  
  
 Quando você solicita um assembly totalmente assinado, o compilador usa o hash no arquivo que contém o manifesto (metadados de assembly) e sinaliza esse hash com a chave particular. A assinatura digital resultante é armazenada no arquivo que contém o manifesto. Quando um assembly é assinado com atraso, o compilador não de computação e armazenar a assinatura, mas as reservas de espaço no arquivo para que a assinatura pode ser adicionada depois.  
  
 Por exemplo, usando `-delaysign+`, um desenvolvedor em uma organização pode distribuir versões de teste sem sinal de um assembly que os testadores podem se registrar com o cache de assembly global e usar. Quando o trabalho no assembly for concluído, a pessoa responsável pela chave privada da organização pode assinar completamente o assembly. Este compartimentalização protege a chave privada da organização contra divulgação, permitindo que todos os desenvolvedores trabalhar em assemblies.  
  
 Ver [criando e usando Assemblies nomes fortes](../../../framework/app-domains/create-and-use-strong-named-assemblies.md) para obter mais informações sobre como assinar um assembly.  
  
### <a name="to-set--delaysign-in-the-visual-studio-integrated-development-environment"></a>Definir - delaysign no ambiente de desenvolvimento integrado do Visual Studio  
  
1. Selecione um projeto no **Gerenciador de Soluções**. No menu **Projeto**, clique em **Propriedades**.   
  
2. Clique na guia **Assinatura**.  
  
3. Defina o valor na **somente sinal de atraso** caixa.  
  
## <a name="see-also"></a>Consulte também

- [Compilador de linha de comando do Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)
- [-keyfile](../../../visual-basic/reference/command-line-compiler/keyfile.md)
- [-keycontainer](../../../visual-basic/reference/command-line-compiler/keycontainer.md)
- [Linhas de comando de compilação de exemplo](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
