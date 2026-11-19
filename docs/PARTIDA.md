# Nexus Inside: documento de partida

Nascido em 19/11/2026, na sala de ideias do Nexus Modeler.

## O que é

Um firmware próprio da família Nexus para pedaleiras multiefeitos. Ele transforma a pedaleira num equipamento Nexus: captura (NAM A2-Lite e, se couber, os modelos do Nexus Modeling Engine), IRs, efeitos, presets e cenas, com a tela e os pisantes do nosso jeito.

Não é o Nexus Modeler rodando na pedaleira. O chip é um microcontrolador, sem Linux nem JUCE. O Nexus Inside é um programa próprio, em C, escrito do zero sobre o SDK público do fabricante do chip.

## Estrutura

```
Família Nexus
├── Nexus Modeler       (computador)
├── Nexus Inside Editor (computador, código fechado): o EDITOR das pedaleiras
└── Nexus Inside        (firmware, código fechado; este repositório guarda a documentação)
    ├── núcleo          motor de áudio em ponto fixo, efeitos, presets, protocolo USB
    └── mods            um por pedaleira: só o que é da placa (tela, pisantes, LEDs, codec, partições)
```

1. **Um núcleo, vários mods.** Pedaleira nova só exige a camada da placa.
2. **O Nexus Inside Editor é o editor.** Programa próprio, separado do Nexus Modeler e com o mesmo visual, para Mac, Windows e Linux. Presets, capturas e IRs vão do computador para qualquer pedaleira com Nexus Inside.
3. **Código fechado** (decisão de 19/11/2026). O repositório é público, mas o código do firmware não é aberto.

## Fases

- **Fase 0, só leitura.** Identificar a placa, testar o modo de carga do chip e tirar a cópia de segurança completa da memória. É o que garante a volta ao firmware original.
- **Fase 1.** Firmware mínimo: acende LED, escreve na tela e volta ao firmware original.
- **Fase 2.** Áudio passando direto da entrada para a saída.
- **Fase 3.** Captura e IR tocando.
- **Fase 4.** Tela, pisantes, presets e o Nexus Inside Editor falando com a pedaleira.

## Decisões pendentes

1. Busca do nome no INPI e no domínio.

## Riscos

- **Inutilizar a pedaleira.** A fase 0 existe para isso: nada é gravado antes de a cópia de segurança completa existir e de o caminho de volta estar provado.
- **Garantia.** Firmware não oficial anula a garantia da pedaleira.
- **Tamanho do trabalho.** É projeto grande, de meses.
