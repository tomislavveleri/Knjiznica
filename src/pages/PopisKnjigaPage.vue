<template>
  <q-page padding>
    <div class="q-pa-md">
      <q-table title="Knjige" :rows="rows" :columns="columns" row-key="name" />
    </div>
  </q-page>
</template>

<script>
const columns = [
  {
    name: "name",
    required: true,
    label: "ID",
    align: "left",
    field: (row) => row.name,
    format: (val) => `${val}`,
    sortable: true,
  },
  {
    name: "naslovKnjige",
    align: "center",
    label: "Naslov Knjige",
    field: (row) => row.naslovKnjige,
    format: (val) => `${val}`,
    sortable: true,
  },
  {
    name: "autor",
    label: "Autor",
    field: "atr",
    field: (row) => row.autor,
    format: (val) => `${val}`,
    sortable: true,
  },
  {
    name: "opis",
    label: "Opis",
    field: (row) => row.opis,
    format: (val) => `${val}`,
  },
  {
    name: "slika",
    label: "Slika",
    field: (row) => row.slika,
    format: (val) => `${val}`,
  },
  {
    name: "stanje",
    label: "Stanje(ukupna broj primjeraka)",
    field: (row) => row.stanje,
    format: (val) => `${val}`,
  },
];

const rows = [
  {
    name: "1",
    naslovKnjige: "Petar Pan",
    autor: "Pero Pavlovic",
    opis: "Prica o letecem djecaku",
    slika: "slika knjige",
    stanje: "da",
  },
  {
    name: "2",
    naslovKnjige: "Alisa u Zemlji Čuda",
    autor: "Ana Novak",
    opis: "Čarobna avantura u neobičnom svijetu",
    slika: "slika alise",
    stanje: "da",
  },
  {
    name: "3",
    naslovKnjige: "Čarobnjak iz Oza",
    autor: "Marko Petrović",
    opis: "Putovanje do čudesnog čarobnjaka",
    slika: "slika oza",
    stanje: "ne",
  },
  {
    name: "4",
    naslovKnjige: "Robinzon Kruso",
    autor: "Ivan Jurković",
    opis: "Preživljavanje na pustom otoku",
    slika: "slika robinzon",
    stanje: "da",
  },
  {
    name: "5",
    naslovKnjige: "Hajduci",
    autor: "Branko Ivanković",
    opis: "Priče o dječjim pustolovinama",
    slika: "slika hajduci",
    stanje: "da",
  },
  {
    name: "6",
    naslovKnjige: "Mali Princ",
    autor: "Stefan Kovačević",
    opis: "Filozofska priča o djetinjstvu",
    slika: "slika mali princ",
    stanje: "ne",
  },
  {
    name: "7",
    naslovKnjige: "Gospodar Prstenova",
    autor: "Nikola Tomić",
    opis: "Epska avantura u Srednjoj Zemlji",
    slika: "slika prstenovi",
    stanje: "da",
  },
  {
    name: "8",
    naslovKnjige: "1001 Noć",
    autor: "Selma Huseinović",
    opis: "Zbirka arapskih bajki",
    slika: "slika 1001 noc",
    stanje: "da",
  },
  {
    name: "9",
    naslovKnjige: "Don Kihot",
    autor: "Vladimir Stanković",
    opis: "Satirična priča o viteškim avanturama",
    slika: "slika kihot",
    stanje: "ne",
  },
  {
    name: "10",
    naslovKnjige: "Vukovi s Aljaske",
    autor: "Petar Kovač",
    opis: "Priča o preživljavanju u divljini",
    slika: "slika vukovi",
    stanje: "da",
  },
];

export default {
  setup() {
    return {
      columns,
      rows,
    };
  },
};
</script>
