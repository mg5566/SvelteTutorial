<script lang="ts">
  import Card from '../../components/templates/Card.svelte';

  let userId = 0;
  let nickName = 'mykang';
  let userProfileMessage = 'fucking exem';
  // - 자신을 표현하는 글, 카톡 상태 메세지 같은 느낌
  let iPAddress;
  let userImage;
</script>

<Card>
  <p slot="title">
    { userId } { nickName }
  </p>
  <p slot="content">
    { userProfileMessage }
  </p>
  <p slot="sub">
    { iPAddress }
  </p>
</Card>