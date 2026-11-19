# Nexus Inside: documento de partida

Nascido em 19/11/2026, na sala de ideias do Nexus Modeler.

## O que é

Um firmware próprio da família Nexus para pedaleiras multiefeitos. Ele transforma a pedaleira num equipamento Nexus: captura (NAM A2-Lite e, se couber, os modelos do Nexus Modeling Engine), IRs, efeitos, presets e cenas, com a tela e os pisantes do nosso jeito.

Não é o Nexus Modeler rodando na pedaleira. O chip é um microcontrolador, sem Linux nem JUCE. O Nexus Inside é um programa próprio, em C, escrito do zero sobre o SDK público do fabricante do chip.

## Estrutura

```
Família Nexus
├── Nexus Modeler       (computador, GPL, público). Também é o EDITOR das pedaleiras.
└── Nexus Inside        (firmware, este repositório)
    ├── núcleo          motor de áudio em ponto fixo, efeitos, presets, protocolo USB
    └── mods            um por pedaleira: só o que é da placa (tela, pisantes, LEDs, codec, partições)
```

1. **Um núcleo, vários mods.** Pedaleira nova só exige a camada da placa.
2. **O Nexus Modeler é o editor.** Presets, capturas e IRs vão do computador para qualquer pedaleira com Nexus Inside.
3. **Licença separada do Nexus Modeler.** O SDK do chip traz bibliotecas fechadas, que não combinam com GPL.

## Fases

- **Fase 0, só leitura.** Identificar a placa, testar o modo de carga do chip e tirar a cópia de segurança completa da memória. É o que garante a volta ao firmware original.
- **Fase 1.** Firmware mínimo: acende LED, escreve na tela e volta ao firmware original.
- **Fase 2.** Áudio passando direto da entrada para a saída.
- **Fase 3.** Captura e IR tocando.
- **Fase 4.** Tela, pisantes, presets e o editor no Nexus Modeler.

## Decisões pendentes

1. Busca do nome no INPI e no domínio.
2. Licença do firmware.

## Riscos

- **Inutilizar a pedaleira.** A fase 0 existe para isso: nada é gravado antes de a cópia de segurança completa existir e de o caminho de volta estar provado.
- **Garantia.** Firmware não oficial anula a garantia da pedaleira.
- **Tamanho do trabalho.** É projeto grande, de meses.
