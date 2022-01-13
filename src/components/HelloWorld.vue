<template>
  <div>
    <div><input type="number" v-model.number="column" @change="re()" /></div>
    <div class="hello">
      <div class="lane" v-for="(d, index) in ds" :key="index">
        <transition-group name="list" tag="div">
          <div class="card" v-for="(e, i) in d" :key="i">
            <h3>{{ e.index }}</h3>
            {{ e.text }}
          </div>
        </transition-group>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "HelloWorld",
  props: {
    msg: String,
  },
  data() {
    return {
      column: 3,
      ds: [],
      raw: [
        `Lorem ipsum dolor sit amet, consectetuer adipiscing elit. Maecenas porttitor congue massa. Fusce posuere, magna sed pulvinar ultricies, purus lectus malesuada libero, sit amet commodo magna eros quis urna.`,
        `Nunc viverra imperdiet enim. Fusce est. Vivamus a tellus.`,
        `Pellentesque habitant morbi tristique senectus et netus et m`,
        `alesuada fames ac turpis egestas., Proin pharetra nonummy pede. Mauris et orci.`,
        `Aenean nec lorem. In porttitor. Donec laoreet nonummy augue.`,
        `Suspendisse dui purus, scelerisque at, vulputate vitae, pretium mattis, nunc. Mauris eget`,
        ` neque at sem venenatis eleifend. Ut nonummy.`,
        `Fusce aliquet pede non pede. Suspendisse dapibus lorem pellentesque magna. Integer nulla.`,
        `Donec blandit feugiat ligula. Donec hendrerit, felis et imperdiet euismod, purus ipsum pretium metus, in lacinia nulla nisl eget sapien. Donec ut est in lectus consequat consequat.`,
        `Etiam eget dui. Aliquam erat volutpat. Sed at lorem in nunc porta tristique.`,
        `Proin nec augue. Quisque aliquam tempor magna. Pellentesque habitant morbi tristique senectus et netus et malesuada f`,
        `Nunc ac magna. Maecenas odio dolor, vulputate vel, auctor ac, accumsan id, felis. Pellentesque cursus sagittis felis.`,
        `Pellentesque porttitor, velit lacinia egestas auctor, diam eros tempus arcu, nec vulputate augue magna vel risus. Cras non magna vel ante adipiscing rhoncus. Vivamus a mi.`,
        `Morbi neque. Aliquam erat volutpat. Integer ultrices lobortis eros.`,
        `Pellentesque habitant morbi tristique senectus et netus et malesuada fames ac turpis egestas., Proin semper, ante vitae sollicitudin posuere, metus quam iaculis nibh, vitae scelerisque nunc massa eget pede. Sed velit urna, interdum vel, ultricies vel, faucibus at, quam.`,
        `Donec elit est, consectetuer eget, consequat quis, tempus quis, wisi. In in nunc. Class aptent taciti sociosqu ad litora torquent per conubia nostra, per inceptos hymenaeos.`,
        `Donec ullamcorper fringilla eros. Fusce in sapien eu purus dapi`,
        `bus commodo. Cum sociis natoque penatibus et magnis dis parturient montes, nascetur ridiculus mus.`,
        `Cras faucibus condimentum odio. Sed ac ligula. Aliquam at eros.`,
        `Etiam at ligula et tellus ullamcorper ultrices. In fermentum, lorem non cursus porttitor, diam urna accumsan lacus, sed interdum wisi nibh nec nisl. Ut tincidunt volutpat urna.`,
        `Mauris eleifend nulla eget mauris. Sed cursus quam id felis. Curabitur posuere quam vel nibh.`,
        `Cras dapibus dapibus nisl. Vestibulum quis dolor a felis congue vehicula. Maecenas pede purus, tristique ac, tempus eget, egestas quis, mauris.`,
        `Curabitur non eros. Nullam hendrerit bibendum justo. Fusce iaculis, est quis lacinia pr`,
        `Quisque ornare placerat risus. Ut molestie magna at mi. Integer aliquet mauris `,
        `Ut mattis ligula posuere velit. Nunc sagittis. Curabitur varius`,
        `Duis pretium mi euismod erat. Maecenas id augue. Nam vulputate.`,
        `Duis a quam non neque lobortis malesuada. Praesent euismod. Donec nulla augue, venenatis scelerisque, dapibus a, consequat at, leo.`,
        `Pellentesque libero lectus, tristique ac, consectetuer sit amet, imperdiet ut, justo. Sed aliquam odio vit`,
        `In hac habitasse platea dictumst. Suspendisse potenti. Vivamus vitae massa adipiscing est lacinia sodales.`,
        `Donec metus massa, mollis vel, tempus placerat, vestibulum condimentum, ligula. Nunc lacus metus, posuere eget, lacinia eu, varius quis, libero. Aliquam nonummy adipiscing augue.`,
        `Lorem ipsum dolor sit amet, consectetuer adipiscing elit. Maecenas porttitor congue massa. Fusce posuere, magna sed pulvinar ultricies, purus lectus malesuada libero, sit amet commodo magna eros quis urna.`,
        `Nunc viverra imperdiet enim. Fusce est. Vivamus a tellus.`,
        `Pellentesque habitant morbi tristique senectus et netus et m`,
        `alesuada f, Proin pharetra nonummy pede. Mauris et orci.`,
        `Aenean nec lorem. In porttitor. Donec laoreet nonummy augue.`,
        `Suspendisse dui purus, scelerisque at, vulputate vitae, pretium mattis, nunc. Mauris eget`,
        ` neque at sem venenatis eleifend. Ut nonummy.`,
        `Fusce aliquet pede non pede. Suspendisse dapibus lorem pellentesque magna. Integer nulla.`,
        `Donec blandit feugiat ligula. Donec hendrerit, felis et imperdiet euismod, purus ipsum pretium metus, in lacinia nulla nisl eget sapien. Donec ut est in lectus consequat consequat.`,
        `Etiam eget dui. Aliquam erat volutpat. Sed at lorem in nunc porta tristique.`,
        `Proin nec augue. Quisque aliquam tempor magna. Pellentesque habitant morbi tristique senectus et netus et malesuada f`,
        ,
        `Nunc ac magna. Maecenas odio dolor, vulputate vel, auctor ac, accumsan id, felis. Pellentesque cursus sagittis felis.`,
        `Pellentesque porttitor, velit lacinia egestas auctor, diam eros tempus arcu, nec vulputate augue magna vel risus. Cras non magna vel ante adipiscing rhoncus. Vivamus a mi.`,
        `Morbi neque. Aliquam erat volutpat. Integer ultrices lobortis eros.`,
        `Pellentesque habitant morbi tristique senectus et netus et malesuada f, Proin semper, ante vitae sollicitudin posuere, metus quam iaculis nibh, vitae scelerisque nunc massa eget pede. Sed velit urna, interdum vel, ultricies vel, faucibus at, quam.`,
        `Donec elit est, consectetuer eget, consequat quis, tempus quis, wisi. In in nunc. Class aptent taciti sociosqu ad litora torquent per conubia nostra, per inceptos hymenaeos.`,
        `Donec ullamcorper fringilla eros. Fusce in sapien eu purus dapi`,
        `bus commodo. Cum sociis natoque penatibus et magnis dis parturient montes, nascetur ridiculus mus.`,
        `Cras faucibus condimentum odio. Sed ac ligula. Aliquam at eros.`,
        `Etiam at ligula et tellus ullamcorper ultrices. In fermentum, lorem non cursus porttitor, diam urna accumsan lacus, sed interdum wisi nibh nec nisl. Ut tincidunt volutpat urna.`,
        `Mauris eleifend nulla eget mauris. Sed cursus quam id felis. Curabitur posuere quam vel nibh.`,
        `Cras dapibus dapibus nisl. Vestibulum quis dolor a felis congue vehicula. Maecenas pede purus, tristique ac, tempus eget, egestas quis, mauris.`,
        `Curabitur non eros. Nullam hendrerit bibendum justo. Fusce iaculis, est quis lacinia pr`,
        `Quisque ornare placerat risus. Ut molestie magna at mi. Integer aliquet mauris `,
        `Ut mattis ligula posuere velit. Nunc sagittis. Curabitur varius`,
        `Duis pretium mi euismod erat. Maecenas id augue. Nam vulputate.`,
        `Duis a quam non neque lobortis malesuada. Praesent euismod. Donec nulla augue, venenatis scelerisque, dapibus a, consequat at, leo.`,
        `Pellentesque libero lectus, tristique ac, consectetuer sit amet, imperdiet ut, justo. Sed aliquam odio vit`,
        `In hac habitasse platea dictumst. Suspendisse potenti. Vivamus vitae massa adipiscing est lacinia sodales.`,
        `Donec metus massa, mollis vel, tempus placerat, vestibulum condimentum, ligula. Nunc lacus metus, posuere eget, lacinia eu, varius quis, libero. Aliquam nonummy adipiscing augue.`,
        `Lorem ipsum dolor sit amet, consectetuer adipiscing elit. Maecenas porttitor congue massa. Fusce posuere, magna sed pulvinar ultricies, purus lectus malesuada libero, sit amet commodo magna eros quis urna.`,
        `Nunc viverra imperdiet enim. Fusce est. Vivamus a tellus.`,
        `Pellentesque habitant morbi tristique senectus et netus et m`,
        `alesuada f, Proin pharetra nonummy pede. Mauris et orci.`,
        `Aenean nec lorem. In porttitor. Donec laoreet nonummy augue.`,
        `Suspendisse dui purus, scelerisque at, vulputate vitae, pretium mattis, nunc. Mauris eget`,
        ` neque at sem venenatis eleifend. Ut nonummy.`,
        `Fusce aliquet pede non pede. Suspendisse dapibus lorem pellentesque magna. Integer nulla.`,
        `Donec blandit feugiat ligula. Donec hendrerit, felis et imperdiet euismod, purus ipsum pretium metus, in lacinia nulla nisl eget sapien. Donec ut est in lectus consequat consequat.`,
        `Etiam eget dui. Aliquam erat volutpat. Sed at lorem in nunc porta tristique.`,
        `Proin nec augue. Quisque aliquam tempor magna. Pellentesque habitant morbi tristique senectus et netus et malesuada f`,
        ,
        `Nunc ac magna. Maecenas odio dolor, vulputate vel, auctor ac, accumsan id, felis. Pellentesque cursus sagittis felis.`,
        `Pellentesque porttitor, velit lacinia egestas auctor, diam eros tempus arcu, nec vulputate augue magna vel risus. Cras non magna vel ante adipiscing rhoncus. Vivamus a mi.`,
        `Morbi neque. Aliquam erat volutpat. Integer ultrices lobortis eros.`,
        `Pellentesque habitant morbi tristique senectus et netus et malesuada f, Proin semper, ante vitae sollicitudin posuere, metus quam iaculis nibh, vitae scelerisque nunc massa eget pede. Sed velit urna, interdum vel, ultricies vel, faucibus at, quam.`,
        `Donec elit est, consectetuer eget, consequat quis, tempus quis, wisi. In in nunc. Class aptent taciti sociosqu ad litora torquent per conubia nostra, per inceptos hymenaeos.`,
        `Donec ullamcorper fringilla eros. Fusce in sapien eu purus dapi`,
        `bus commodo. Cum sociis natoque penatibus et magnis dis parturient montes, nascetur ridiculus mus.`,
        `Cras faucibus condimentum odio. Sed ac ligula. Aliquam at eros.`,
        `Etiam at ligula et tellus ullamcorper ultrices. In fermentum, lorem non cursus porttitor, diam urna accumsan lacus, sed interdum wisi nibh nec nisl. Ut tincidunt volutpat urna.`,
        `Mauris eleifend nulla eget mauris. Sed cursus quam id felis. Curabitur posuere quam vel nibh.`,
        `Cras dapibus dapibus nisl. Vestibulum quis dolor a felis congue vehicula. Maecenas pede purus, tristique ac, tempus eget, egestas quis, mauris.`,
        `Curabitur non eros. Nullam hendrerit bibendum justo. Fusce iaculis, est quis lacinia pr`,
        `Duis pretium mi euismod erat. Maecenas id augue. Nam vulputate.`,
        `Duis a quam non neque lobortis malesuada. Praesent euismod. Donec nulla augue, venenatis scelerisque, dapibus a, consequat at, leo.`,
        `Pellentesque libero lectus, tristique ac, consectetuer sit amet, imperdiet ut, justo. Sed aliquam odio vit`,
        `In hac habitasse platea dictumst. Suspendisse potenti. Vivamus vitae massa adipiscing est lacinia sodales.`,
        `Donec metus massa, mollis vel, tempus placerat, vestibulum condimentum, ligula. Nunc lacus metus, posuere eget, lacinia eu, varius quis, libero. Aliquam nonummy adipiscing augue.`,
        `Lorem ipsum dolor sit amet, consectetuer adipiscing elit. Maecenas porttitor congue massa. Fusce posuere, magna sed pulvinar ultricies, purus lectus malesuada libero, sit amet commodo magna eros quis urna.`,
        `Nunc viverra imperdiet enim. Fusce est. Vivamus a tellus.`,
        `Pellentesque habitant morbi tristique senectus et netus et m`,
        `alesuada f, Proin pharetra nonummy pede. Mauris et orci.`,
        `Aenean nec lorem. In porttitor. Donec laoreet nonummy augue.`,
        `Suspendisse dui purus, scelerisque at, vulputate vitae, pretium mattis, nunc. Mauris eget`,
        ` neque at sem venenatis eleifend. Ut nonummy.`,
        `Fusce aliquet pede non pede. Suspendisse dapibus lorem pellentesque magna. Integer nulla.`,
        `Donec blandit feugiat ligula. Donec hendrerit, felis et imperdiet euismod, purus ipsum pretium metus, in lacinia nulla nisl eget sapien. Donec ut est in lectus consequat consequat.`,
        `Etiam eget dui. Aliquam erat volutpat. Sed at lorem in nunc porta tristique.`,
        `Proin nec augue. Quisque aliquam tempor magna. Pellentesque habitant morbi tristique senectus et netus et malesuada f`,
        ,
        `Nunc ac magna. Maecenas odio dolor, vulputate vel, auctor ac, accumsan id, felis. Pellentesque cursus sagittis felis.`,
        `Pellentesque porttitor, velit lacinia egestas auctor, diam eros tempus arcu, nec vulputate augue magna vel risus. Cras non magna vel ante adipiscing rhoncus. Vivamus a mi.`,
        `Morbi neque. Aliquam erat volutpat. Integer ultrices lobortis eros.`,
        `Pellentesque habitant morbi tristique senectus et netus et malesuada f, Proin semper, ante vitae sollicitudin posuere, metus quam iaculis nibh, vitae scelerisque nunc massa eget pede. Sed velit urna, interdum vel, ultricies vel, faucibus at, quam.`,
        `Donec elit est, consectetuer eget, consequat quis, tempus quis, wisi. In in nunc. Class aptent taciti sociosqu ad litora torquent per conubia nostra, per inceptos hymenaeos.`,
        `Donec ullamcorper fringilla eros. Fusce in sapien eu purus dapi`,
        `bus commodo. Cum sociis natoque penatibus et magnis dis parturient montes, nascetur ridiculus mus.`,
        `Cras faucibus condimentum odio. Sed ac ligula. Aliquam at eros.`,
        `Etiam at ligula et tellus ullamcorper ultrices. In fermentum, lorem non cursus porttitor, diam urna accumsan lacus, sed interdum wisi nibh nec nisl. Ut tincidunt volutpat urna.`,
        `Mauris eleifend nulla eget mauris. Sed cursus quam id felis. Curabitur posuere quam vel nibh.`,
        `Cras dapibus dapibus nisl. Vestibulum quis dolor a felis congue vehicula. Maecenas pede purus, tristique ac, tempus eget, egestas quis, mauris.`,
        `Curabitur non eros. Nullam hendrerit bibendum justo. Fusce iaculis, est quis lacinia pr`,
        `Duis pretium mi euismod erat. Maecenas id augue. Nam vulputate.`,
        `Duis a quam non neque lobortis malesuada. Praesent euismod. Donec nulla augue, venenatis scelerisque, dapibus a, consequat at, leo.`,
        `Pellentesque libero lectus, tristique ac, consectetuer sit amet, imperdiet ut, justo. Sed aliquam odio vit`,
        `In hac habitasse platea dictumst. Suspendisse potenti. Vivamus vitae massa adipiscing est lacinia sodales.`,
        `Donec metus massa, mollis vel, tempus placerat, vestibulum condimentum, ligula. Nunc lacus metus, posuere eget, lacinia eu, varius quis, libero. Aliquam nonummy adipiscing augue.`,
        `Lorem ipsum dolor sit amet, consectetuer adipiscing elit. Maecenas porttitor congue massa. Fusce posuere, magna sed pulvinar ultricies, purus lectus malesuada libero, sit amet commodo magna eros quis urna.`,
        `Nunc viverra imperdiet enim. Fusce est. Vivamus a tellus.`,
        `Pellentesque habitant morbi tristique senectus et netus et m`,
        `alesuada f, Proin pharetra nonummy pede. Mauris et orci.`,
        `Aenean nec lorem. In porttitor. Donec laoreet nonummy augue.`,
        `Suspendisse dui purus, scelerisque at, vulputate vitae, pretium mattis, nunc. Mauris eget`,
        ` neque at sem venenatis eleifend. Ut nonummy.`,
        `Fusce aliquet pede non pede. Suspendisse dapibus lorem pellentesque magna. Integer nulla.`,
        `Donec blandit feugiat ligula. Donec hendrerit, felis et imperdiet euismod, purus ipsum pretium metus, in lacinia nulla nisl eget sapien. Donec ut est in lectus consequat consequat.`,
        `Etiam eget dui. Aliquam erat volutpat. Sed at lorem in nunc porta tristique.`,
        `Proin nec augue. Quisque aliquam tempor magna. Pellentesque habitant morbi tristique senectus et netus et malesuada f`,
        `Nunc ac magna. Maecenas odio dolor, vulputate vel, auctor ac, accumsan id, felis. Pellentesque cursus sagittis felis.`,
        `Pellentesque porttitor, velit lacinia egestas auctor, diam eros tempus arcu, nec vulputate augue magna vel risus. Cras non magna vel ante adipiscing rhoncus. Vivamus a mi.`,
        `Morbi neque. Aliquam erat volutpat. Integer ultrices lobortis eros.`,
        `Pellentesque habitant morbi tristique senectus et netus et malesuada f, Proin semper, ante vitae sollicitudin posuere, metus quam iaculis nibh, vitae scelerisque nunc massa eget pede. Sed velit urna, interdum vel, ultricies vel, faucibus at, quam.`,
        `Donec elit est, consectetuer eget, consequat quis, tempus quis, wisi. In in nunc. Class aptent taciti sociosqu ad litora torquent per conubia nostra, per inceptos hymenaeos.`,
        `Donec ullamcorper fringilla eros. Fusce in sapien eu purus dapi`,
        `bus commodo. Cum sociis natoque penatibus et magnis dis parturient montes, nascetur ridiculus mus.`,
        `Cras faucibus condimentum odio. Sed ac ligula. Aliquam at eros.`,
        `Etiam at ligula et tellus ullamcorper ultrices. In fermentum, lorem non cursus porttitor, diam urna accumsan lacus, sed interdum wisi nibh nec nisl. Ut tincidunt volutpat urna.`,
        `Mauris eleifend nulla eget mauris. Sed cursus quam id felis. Curabitur posuere quam vel nibh.`,
        `Cras dapibus dapibus nisl. Vestibulum quis dolor a felis congue vehicula. Maecenas pede purus, tristique ac, tempus eget, egestas quis, mauris.`,
        `Curabitur non eros. Nullam hendrerit bibendum justo. Fusce iaculis, est quis lacinia pr`,
        `Duis pretium mi euismod erat. Maecenas id augue. Nam vulputate.`,
        `Duis a quam non neque lobortis malesuada. Praesent euismod. Donec nulla augue, venenatis scelerisque, dapibus a, consequat at, leo.`,
        `Pellentesque libero lectus, tristique ac, consectetuer sit amet, imperdiet ut, justo. Sed aliquam odio vit`,
        `In hac habitasse platea dictumst. Suspendisse potenti. Vivamus vitae massa adipiscing est lacinia sodales.`,
        `Donec metus massa, mollis vel, tempus placerat, vestibulum condimentum, ligula. Nunc lacus metus, posuere eget, lacinia eu, varius quis, libero. Aliquam nonummy adipiscing augue.`,
        `Lorem ipsum dolor sit amet, consectetuer adipiscing elit. Maecenas porttitor congue massa. Fusce posuere, magna sed pulvinar ultricies, purus lectus malesuada libero, sit amet commodo magna eros quis urna.`,
        `Nunc viverra imperdiet enim. Fusce est. Vivamus a tellus.`,
        `Pellentesque habitant morbi tristique senectus et netus et m`,
        `alesuada f, Proin pharetra nonummy pede. Mauris et orci.`,
        `Aenean nec lorem. In porttitor. Donec laoreet nonummy augue.`,
        `Suspendisse dui purus, scelerisque at, vulputate vitae, pretium mattis, nunc. Mauris eget`,
        ` neque at sem venenatis eleifend. Ut nonummy.`,
        `Fusce aliquet pede non pede. Suspendisse dapibus lorem pellentesque magna. Integer nulla.`,
        `Donec blandit feugiat ligula. Donec hendrerit, felis et imperdiet euismod, purus ipsum pretium metus, in lacinia nulla nisl eget sapien. Donec ut est in lectus consequat consequat.`,
        `Etiam eget dui. Aliquam erat volutpat. Sed at lorem in nunc porta tristique.`,
        `Proin nec augue. Quisque aliquam tempor magna. Pellentesque habitant morbi tristique senectus et netus et malesuada f`,
        `Nunc ac magna. Maecenas odio dolor, vulputate vel, auctor ac, accumsan id, felis. Pellentesque cursus sagittis felis.`,
        `Pellentesque porttitor, velit lacinia egestas auctor, diam eros tempus arcu, nec vulputate augue magna vel risus. Cras non magna vel ante adipiscing rhoncus. Vivamus a mi.`,
        `Morbi neque. Aliquam erat volutpat. Integer ultrices lobortis eros.`,
        `Pellentesque habitant morbi tristique senectus et netus et malesuada f, Proin semper, ante vitae sollicitudin posuere, metus quam iaculis nibh, vitae scelerisque nunc massa eget pede. Sed velit urna, interdum vel, ultricies vel, faucibus at, quam.`,
        `Donec elit est, consectetuer eget, consequat quis, tempus quis, wisi. In in nunc. Class aptent taciti sociosqu ad litora torquent per conubia nostra, per inceptos hymenaeos.`,
        `Donec ullamcorper fringilla eros. Fusce in sapien eu purus dapi`,
        `bus commodo. Cum sociis natoque penatibus et magnis dis parturient montes, nascetur ridiculus mus.`,
        `Cras faucibus condimentum odio. Sed ac ligula. Aliquam at eros.`,
        `Etiam at ligula et tellus ullamcorper ultrices. In fermentum, lorem non cursus porttitor, diam urna accumsan lacus, sed interdum wisi nibh nec nisl. Ut tincidunt volutpat urna.`,
        `Mauris eleifend nulla eget mauris. Sed cursus quam id felis. Curabitur posuere quam vel nibh.`,
        `Cras dapibus dapibus nisl. Vestibulum quis dolor a felis congue vehicula. Maecenas pede purus, tristique ac, tempus eget, egestas quis, mauris.`,
        `Curabitur non eros. Nullam hendrerit bibendum justo. Fusce iaculis, est quis lacinia pr`,
        `Duis pretium mi euismod erat. Maecenas id augue. Nam vulputate.`,
        `Duis a quam non neque lobortis malesuada. Praesent euismod. Donec nulla augue, venenatis scelerisque, dapibus a, consequat at, leo.`,
        `Pellentesque libero lectus, tristique ac, consectetuer sit amet, imperdiet ut, justo. Sed aliquam odio vit`,
        `In hac habitasse platea dictumst. Suspendisse potenti. Vivamus vitae massa adipiscing est lacinia sodales.`,
        `Donec metus massa, mollis vel, tempus placerat, vestibulum condimentum, ligula. Nunc lacus metus, posuere eget, lacinia eu, varius quis, libero. Aliquam nonummy adipiscing augue.`,
        `Lorem ipsum dolor sit amet, consectetuer adipiscing elit. Maecenas porttitor congue massa. Fusce posuere, magna sed pulvinar ultricies, purus lectus malesuada libero, sit amet commodo magna eros quis urna.`,
        `Nunc viverra imperdiet enim. Fusce est. Vivamus a tellus.`,
        `Pellentesque habitant morbi tristique senectus et netus et m`,
        `alesuada f, Proin pharetra nonummy pede. Mauris et orci.`,
        `Aenean nec lorem. In porttitor. Donec laoreet nonummy augue.`,
        `Suspendisse dui purus, scelerisque at, vulputate vitae, pretium mattis, nunc. Mauris eget`,
        ` neque at sem venenatis eleifend. Ut nonummy.`,
        `Fusce aliquet pede non pede. Suspendisse dapibus lorem pellentesque magna. Integer nulla.`,
        `Donec blandit feugiat ligula. Donec hendrerit, felis et imperdiet euismod, purus ipsum pretium metus, in lacinia nulla nisl eget sapien. Donec ut est in lectus consequat consequat.`,
        `Etiam eget dui. Aliquam erat volutpat. Sed at lorem in nunc porta tristique.`,
        `Proin nec augue. Quisque aliquam tempor magna. Pellentesque habitant morbi tristique senectus et netus et malesuada f`,
        `Nunc ac magna. Maecenas odio dolor, vulputate vel, auctor ac, accumsan id, felis. Pellentesque cursus sagittis felis.`,
        `Pellentesque porttitor, velit lacinia egestas auctor, diam eros tempus arcu, nec vulputate augue magna vel risus. Cras non magna vel ante adipiscing rhoncus. Vivamus a mi.`,
        `Morbi neque. Aliquam erat volutpat. Integer ultrices lobortis eros.`,
        `Pellentesque habitant morbi tristique senectus et netus et malesuada f, Proin semper, ante vitae sollicitudin posuere, metus quam iaculis nibh, vitae scelerisque nunc massa eget pede. Sed velit urna, interdum vel, ultricies vel, faucibus at, quam.`,
        `Donec elit est, consectetuer eget, consequat quis, tempus quis, wisi. In in nunc. Class aptent taciti sociosqu ad litora torquent per conubia nostra, per inceptos hymenaeos.`,
        `Donec ullamcorper fringilla eros. Fusce in sapien eu purus dapi`,
        `bus commodo. Cum sociis natoque penatibus et magnis dis parturient montes, nascetur ridiculus mus.`,
        `Cras faucibus condimentum odio. Sed ac ligula. Aliquam at eros.`,
        `Etiam at ligula et tellus ullamcorper ultrices. In fermentum, lorem non cursus porttitor, diam urna accumsan lacus, sed interdum wisi nibh nec nisl. Ut tincidunt volutpat urna.`,
        `Mauris eleifend nulla eget mauris. Sed cursus quam id felis. Curabitur posuere quam vel nibh.`,
        `Cras dapibus dapibus nisl. Vestibulum quis dolor a felis congue vehicula. Maecenas pede purus, tristique ac, tempus eget, egestas quis, mauris.`,
        `Curabitur non eros. Nullam hendrerit bibendum justo. Fusce iaculis, est quis lacinia pr`,
        `Duis pretium mi euismod erat. Maecenas id augue. Nam vulputate.`,
        `Duis a quam non neque lobortis malesuada. Praesent euismod. Donec nulla augue, venenatis scelerisque, dapibus a, consequat at, leo.`,
        `Pellentesque libero lectus, tristique ac, consectetuer sit amet, imperdiet ut, justo. Sed aliquam odio vit`,
        `In hac habitasse platea dictumst. Suspendisse potenti. Vivamus vitae massa adipiscing est lacinia sodales.`,
        `Donec metus massa, mollis vel, tempus placerat, vestibulum condimentum, ligula. Nunc lacus metus, posuere eget, lacinia eu, varius quis, libero. Aliquam nonummy adipiscing augue.`,
        `Lorem ipsum dolor sit amet, consectetuer adipiscing elit. Maecenas porttitor congue massa. Fusce posuere, magna sed pulvinar ultricies, purus lectus malesuada libero, sit amet commodo magna eros quis urna.`,
        `Nunc viverra imperdiet enim. Fusce est. Vivamus a tellus.`,
        `Pellentesque habitant morbi tristique senectus et netus et m`,
        `alesuada f, Proin pharetra nonummy pede. Mauris et orci.`,
        `Aenean nec lorem. In porttitor. Donec laoreet nonummy augue.`,
        `Suspendisse dui purus, scelerisque at, vulputate vitae, pretium mattis, nunc. Mauris eget`,
        ` neque at sem venenatis eleifend. Ut nonummy.`,
        `Fusce aliquet pede non pede. Suspendisse dapibus lorem pellentesque magna. Integer nulla.`,
        `Donec blandit feugiat ligula. Donec hendrerit, felis et imperdiet euismod, purus ipsum pretium metus, in lacinia nulla nisl eget sapien. Donec ut est in lectus consequat consequat.`,
        `Etiam eget dui. Aliquam erat volutpat. Sed at lorem in nunc porta tristique.`,
        `Proin nec augue. Quisque aliquam tempor magna. Pellentesque habitant morbi tristique senectus et netus et malesuada f`,
        `Nunc ac magna. Maecenas odio dolor, vulputate vel, auctor ac, accumsan id, felis. Pellentesque cursus sagittis felis.`,
        `Pellentesque porttitor, velit lacinia egestas auctor, diam eros tempus arcu, nec vulputate augue magna vel risus. Cras non magna vel ante adipiscing rhoncus. V`,
        `ivamus a mi.`,
      ],
    };
  },
  methods: {
    re() {
      const c = this.column;
      this.ds = [...Array(c)].map(() => []);
      const ds = this.ds;
      const raw = this.raw.map((v, index) => {
        return { index, text: v };
      });
      this.ds = ds.map((d, i) => raw.filter((r, index) => index % c == i));
    },
  },
  created() {
    this.re();
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.hello {
  display: flex;
}
.lane {
  display: flex;
  flex-direction: column;
}
.card {
  padding: 20px;
  border: 1px solid;
  margin: 10px;
}
.list-item {
  display: inline-block;
  margin-right: 10px;
}
.list-enter-active,
.list-leave-active {
  transition: all 1s;
}
.list-enter, .list-leave-to /* .list-leave-active for below version 2.1.8 */ {
  opacity: 0;
  transform: translateY(30px);
}
.list-move {
  transition: transform 0.5s;
}
</style>
