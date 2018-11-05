---
title: Segurança do provedor de tipos
description: 'Saiba mais sobre a segurança do provedor de tipos em F #, incluindo como alterar as configurações de confiança para um provedor de tipo.'
ms.date: 05/16/2016
ms.openlocfilehash: 26f95ad3950b37a668c497f293b9941ed13a18c7
ms.sourcegitcommit: db8b83057d052c1f9f249d128b08d4423af0f7c2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/02/2018
ms.locfileid: "43861901"
---
# <a name="type-provider-security"></a>Segurança do provedor de tipos

Provedores de tipos são assemblies (DLLs) referenciados pelo seu projeto F # ou script que contêm código para se conectar a fontes de dados externas e revelar essas informações de tipo para o ambiente de tipo F #. Normalmente, o código nos assemblies referenciados somente é executado quando você compila e, em seguida, execute o código (ou no caso de um script, envia o código para o F # interativo). No entanto, um assembly do provedor de tipo será executado dentro do Visual Studio quando o código for simplesmente navegar no editor. Isso acontece porque os provedores de tipos precisam executar para adicionar informações extras para o editor, como dicas de ferramenta informações rápidas, conclusões de IntelliSense e assim por diante. Como resultado, há considerações de segurança extra para o tipo de assemblies do provedor, como eles são executados automaticamente dentro do processo do Visual Studio.

## <a name="security-warning-dialog"></a>Caixa de diálogo de aviso de segurança

Ao usar um assembly do provedor de tipo específico pela primeira vez, o Visual Studio exibe uma caixa de diálogo de segurança que avisa que o provedor de tipos está prestes a executar. Antes do Visual Studio carrega o provedor de tipo, ele dá a oportunidade de decidir se você confiar neste provedor específico. Se você confiar na origem do provedor de tipo, em seguida, selecione "Posso confiar neste provedor de tipo." Se você não confiar na origem do provedor de tipo, em seguida, selecione "Eu não confiar neste provedor de tipo". Confiantes o provedor permite que ele seja executado dentro do Visual Studio e fornecer o IntelliSense e criar recursos. Mas, se o provedor de tipos é mal-intencionado, executar seu código pode comprometer a sua máquina.

Se seu projeto contém código que faz referência a provedores de tipos que você escolheu na caixa de diálogo para não confiar, em seguida, em tempo de compilação, o compilador reportará um erro que indica que o provedor de tipo não é confiável. Quaisquer tipos que são dependentes no provedor de tipo não confiáveis são indicados por linhas onduladas vermelhas. É seguro procurar o código no editor.

Se você decidir alterar a configuração de confiança diretamente no Visual Studio, execute as seguintes etapas.

### <a name="to-change-the-trust-settings-for-type-providers"></a>Para alterar as configurações de confiança para provedores de tipos

1. Sobre o `Tools` menu, selecione `Options`e expanda o `F# Tools` nó.

2. Selecione `Type Providers`, na lista de provedores de tipos, marque a caixa de seleção de provedores de tipos que você confia e desmarque a caixa de seleção para aqueles que você não confia.

## <a name="see-also"></a>Consulte também

- [Provedores de Tipos](index.md)
