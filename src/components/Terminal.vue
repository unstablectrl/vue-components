<template>
  <div id="terminal">
    <header>
      <section class="actions">
        <div class="action close"></div>
        <div class="action minimize"></div>
        <div class="action maximize"></div>
      </section>
      <section class="title">
        <span>zsh</span>
      </section>
    </header>
    <section>
      <span>
        ⚡️
        <strong>~</strong> echo Hello World!
      </span>
    </section>
  </div>
</template>

<script>
export default {};
</script>

<style scoped>
#terminal {
  padding: 5px;
  background: linear-gradient(
    rgb(45, 43, 85) 3%,
    rgb(135, 46, 171) 65%,
    rgb(145, 0, 255) 97%
  );
  border: 1px solid rgb(80, 80, 80);
  border-radius: 5px;
}

#terminal > header {
  display: grid;
  grid-template-columns: 60px 1fr 60px;
  /* background-color: blueviolet; */
}

#terminal > header > .actions {
  display: flex;
  justify-content: center;
  align-items: center;
  /* background-color: cyan; */
}

#terminal > header > .actions > .action {
  height: 12.5px;
  width: 12.5px;
  border-radius: 50%;
  display: block;
  margin: 0 3.5px;
}

#terminal > header > .actions > .action.close {
  background-color: rgb(237, 101, 89);
}

#terminal > header > .actions > .action.minimize {
  background-color: rgb(224, 192, 76);
}

#terminal > header > .actions > .action.maximize {
  background-color: rgb(114, 191, 71);
}

#terminal > header > .title {
  display: flex;
  justify-content: center;
  align-items: center;
  line-height: 1rem;
  /* background-color: limegreen; */
}

#terminal > section {
  padding: 15px 0px;
}
</style>
