# Soporte-android
// Crear un PendingIntent para cada acción
Intent verPerfilIntent = new Intent(this, MainActivity.class);
verPerfilIntent.setAction("VER_PERFIL");
PendingIntent verPerfilPendingIntent = PendingIntent.getActivity(this, 0, verPerfilIntent, PendingIntent.FLAG_UPDATE_CURRENT);

Intent followUnfollowIntent = new Intent(this, FollowUnfollowActivity.class);
followUnfollowIntent.setAction("FOLLOW_UNFOLLOW");
PendingIntent followUnfollowPendingIntent = PendingIntent.getActivity(this, 0, followUnfollowIntent, PendingIntent.FLAG_UPDATE_CURRENT);

Intent verUsuarioIntent = new Intent(this, VerUsuarioActivity.class);
verUsuarioIntent.setAction("VER_USUARIO");
PendingIntent verUsuarioPendingIntent = PendingIntent.getActivity(this, 0, verUsuarioIntent, PendingIntent.FLAG_UPDATE_CURRENT);

// Configurar las acciones en la notificación
NotificationCompat.Builder builder = new NotificationCompat.Builder(this, CHANNEL_ID)
        .setSmallIcon(R.drawable.ic_notification)
        .setContentTitle("Nuevo Like")
        .setContentText("Alguien dio like a tu foto")
        .addAction(R.drawable.ic_ver_perfil, "Ver mi Perfil", verPerfilPendingIntent)
        .addAction(R.drawable.ic_follow_unfollow, "Dar Follow/Unfollow", followUnfollowPendingIntent)
        .addAction(R.drawable.ic_ver_usuario, "Ver Usuario", verUsuarioPendingIntent);

// Mostrar la notificación
NotificationManagerCompat notificationManager = NotificationManagerCompat.from(this);
notificationManager.notify(notificationId, builder.build());
