<script lang="ts">
import DisplayChat from '../../components/organisms/chat/DisplayChat.svelte';
import InputChat from '../../components/organisms/chat/InputChat.svelte';
import io from 'socket.io-client';

// state
let socket_candidates;


const server_socket = io('http://localhost:8080/chat');

server_socket.emit('joinRoom');
server_socket.on('candidates', (candidates) => {
  socket_candidates = candidates;
  console.log('candidates', candidates);
});

// A는 먼저 RTCPeerConnection을 생성하고, ICE 후보와 SDP offer를 생성합니다.
// A는 SDP offer를 Signaling 서버를 통해 B에게 전달합니다.
server_socket.emit('offer', 'client emit - offer');

// B는 SDP offer를 수신하고, RTCPeerConnection을 생성하고, ICE 후보를 생성합니다.
// B는 SDP offer를 바탕으로 SDP answer를 생성하고, Signaling 서버를 통해 A에게 전달합니다.
server_socket.on('answer', (B_answer) => {
  console.log('answer', B_answer);
});

server_socket.emit('answer', 'A SDP');

server_socket.emit('answer', 'client emit - answer');
</script>

<DisplayChat>
</DisplayChat>
{ socket_candidates }
<InputChat>
</InputChat>

<style>
</style>