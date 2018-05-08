---
title: Segurança do provedor de tipos
description: 'Saiba mais sobre a segurança de tipo de provedor em F #, incluindo como alterar as configurações de confiança para um provedor de tipo.'
ms.date: 05/16/2016
ms.openlocfilehash: 66a873a32029d706f1f6fab50dd4f93bc29bca03
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="type-provider-security"></a>Segurança do provedor de tipos

Provedores de tipos são assemblies (DLLs) referenciados pelo projeto F # ou script que contém código para se conectar a fontes de dados externas e essas informações de tipo de superfície para o ambiente do tipo F #. Normalmente, o código em assemblies referenciados é executado somente quando você compila e executar o código (ou no caso de um script, envia o código para F # interativo). No entanto, um assembly do provedor de tipo será executado dentro do Visual Studio quando o código é simplesmente procurado no editor. Isso ocorre porque os provedores de tipos precisam executar para adicionar informações extras no Editor, como dicas de ferramenta informações rápidas, conclusões de IntelliSense e assim por diante. Como resultado, há considerações de segurança adicional para o tipo de assemblies do provedor, desde que eles automaticamente executados dentro do processo do Visual Studio.


## <a name="security-warning-dialog"></a>Caixa de diálogo de aviso de segurança
Ao usar um assembly do provedor de tipo específico pela primeira vez, o Visual Studio exibe uma caixa de diálogo de segurança que avisa que o provedor de tipo está prestes a ser executado. Antes que o Visual Studio carrega o provedor de tipo, isso lhe dá a oportunidade de decidir se você confiar nesse provedor específico. Se você confiar na origem do provedor de tipo, em seguida, selecione "Devo confiar neste provedor de tipo". Se você não confiar na origem do provedor de tipo, em seguida, selecione "Eu não confiar neste provedor de tipo". Confiar o provedor permite executar dentro do Visual Studio e fornecer o IntelliSense e recursos de compilação. Mas, se o provedor de tipos é mal-intencionado, executar seu código poderia comprometer o computador.

Se seu projeto contém o código que faz referência a provedores de tipos que você escolheu na caixa de diálogo não confiar, em seguida, em tempo de compilação, o compilador relatará um erro que indica que o provedor de tipo não é confiável. Quaisquer tipos que são dependentes no provedor de tipo não confiáveis são indicados por linhas onduladas vermelhas. É seguro procurar o código no editor.

Se você decidir alterar a configuração de confiança diretamente no Visual Studio, execute as etapas a seguir.


#### <a name="to-change-the-trust-settings-for-type-providers"></a>Para alterar as configurações de confiança para provedores de tipos

1. Sobre o `Tools` menu, selecione `Options`e expanda o `F# Tools` nó.
<br />

2. Selecione `Type Providers`, na lista de provedores de tipos, marque a caixa de seleção de provedores de tipos que você confia e desmarque a caixa de seleção para aqueles que você não confia.
<br />


## <a name="see-also"></a>Consulte também
[Provedores de Tipos](index.md)
